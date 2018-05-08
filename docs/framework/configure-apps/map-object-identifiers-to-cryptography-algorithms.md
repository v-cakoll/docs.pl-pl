---
title: Mapowanie identyfikatorów obiektów na algorytmy kryptografii
ms.date: 03/30/2017
helpviewer_keywords:
- digital signatures
- identifiers, mapping object identifiers
- cryptographic algorithms
- mapping object identifiers
- cryptography, mapping object identifiers
ms.assetid: c9673f81-bf9e-47fd-bc6f-6bc1c1c4c15e
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 7801c55cf6b3334347788013d9052038d5d2f3ec
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a>Mapowanie identyfikatorów obiektów na algorytmy kryptografii
Podpisy cyfrowe upewnij się, że dane nie jest modyfikowany podczas wysyłania pomiędzy programami do innego. Zwykle podpis cyfrowy jest obliczana przez zastosowanie funkcji matematycznych do wyznaczania wartości skrótu danych do podpisania. Podczas formatowania wartości skrótu, aby były podpisane niektóre algorytmy podpisu cyfrowego Dołącz ASN.1 identyfikatora obiektu (OID) w ramach operacji formatowania. OID Określa algorytm używany do obliczania skrótu. Algorytmy można mapować do identyfikatorów obiektów rozszerzenie mechanizmu kryptografii użycia niestandardowego algorytmów. Poniższy przykład przedstawia sposób odwzorowywania identyfikator obiektu nowego algorytmu wyznaczania wartości skrótu.  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass MyNewHash="MyNewHashClass, MyAssembly  
                  Culture='en', PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="NewHash" class="MyNewHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.14.33.42.46"  name="NewHash"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
 [ \<Oidentry — > element](../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md) zawiera dwa atrybuty. **OID** atrybut jest numer identyfikatora obiektu. **Nazwa** atrybutu jest wartością **nazwa** atrybutu z [ \<nameentry — > elementu](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md). Mapowanie nazw algorytmu do klasy musi istnieć, przed identyfikatorem obiektu mogą być mapowane na prostą nazwą.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie klas kryptografii](../../../docs/framework/configure-apps/configure-cryptography-classes.md)  
 [Usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md)
