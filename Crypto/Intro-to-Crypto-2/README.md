# Writeup
The challenge description hints that both primes are huge and therefore quite similar. To find p and q, one can use the fermats-factorisation.
```python
def fermat(n):
    a = isqrt(n)
    b2 = a*a - n
    b = isqrt(n)
    count = 0
    while b*b != b2:
        a = a + 1
        b2 = a*a - n
        b = isqrt(b2)
        count += 1
    p = a+b
    q = a-b
    assert n == p * q
    return p, q
```
After calculating p and q the rest of the calculation follows the normal pattern.
```python
from Crypto.Util.number import inverse
from gmpy2 import isqrt

m = 6213639477312598145146606285597413094756028916460209994926376562685721597532354994527411261035070313371565996179096901618661905020103824302567694878011247857685359643790779936360396061892681963343509949795893998949164356297380564973147847768251471545846793414196863838506235390508670540548621210855302903513284961283614161501466772253041178512706947379642827461605012461899803919210999488026352375214758873859352222530502137358426056819293786590877544792321648180554981415658300194184367096348141488594780860400420776664995973439686986538967952922269183014996803258574382869102287844486447643771783747439478831567060

e = 65537

N = 11081631875903145989449935723431993312048263659503073501368579288661507666926127398551161494057149306128113773163942639308834214121175806650609216999457699806761832905200688030797211656004392019494461369905299150414106039926917206543955359193966893148964232596310365304968051716316421386564037673515738090636958039103706945349258789436043666088184674948218539196263599899299117746103356732914111330139176914363944699056706536973601851519543254647327613986429683489937828404640743341705415177790924588759219148196121101333618974290049804819348181073769764832469557718828674823915162708288827812462173689965257895702511


def fermat(n):
    a = isqrt(n)
    b2 = a*a - n
    b = isqrt(n)
    count = 0
    while b*b != b2:
        a = a + 1
        b2 = a*a - n
        b = isqrt(b2)
        count += 1
    p = a+b
    q = a-b
    assert n == p * q
    return p, q

#p, q = fermat(N)

p = 105269330176947292996638200435938306898008923026214454261833875185727477089897046111427146733705930821830266909665628457524081078905360676252447567252776868229878866771906188152589974886284283170888631961882151644823439854179072943695999068501018297820499189273623372907923121271707038222250931356234064574969

q = 105269330176947292996638200435938306898008923026214454261833875185727477089897046111427146733705930821830266909665628457524081078905360676252447567252776868229878866771906188152589974886284283170888631961882151644823439854179072943695999068501018297820499189273623372907923121271707038222250931356234064474919


phi = (p-1) * (q-1)

d = inverse(e, phi)

decrypted = pow(m, d, N)
print(hex(decrypted))
```
# Prevention
Both primes should be carefully chosen. Both should be big enough that you cannot bruteforce one of them and they should not be too similar.