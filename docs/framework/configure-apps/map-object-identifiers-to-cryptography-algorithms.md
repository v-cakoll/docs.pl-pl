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
ms.openlocfilehash: a5aebac2d392d4540581dfe7c7afff0819968ac0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912539"
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a>Mapowanie identyfikatorów obiektów na algorytmy kryptografii
Podpisy cyfrowe zapewniają, że dane nie są modyfikowane, gdy są wysyłane z jednego programu do drugiego. Zwykle podpis cyfrowy jest obliczany przez zastosowanie funkcji matematycznej do skrótu danych do podpisania. Podczas formatowania wartości skrótu do podpisania niektóre algorytmy podpisu cyfrowego dołączają identyfikator (OID) ASN. 1 jako część operacji formatowania. Identyfikator OID identyfikuje algorytm używany do obliczania skrótu. Można mapować algorytmy do identyfikatorów obiektów, aby zwiększyć mechanizm kryptografii do korzystania z algorytmów niestandardowych. Poniższy przykład przedstawia sposób mapowania identyfikatora obiektu na nowy algorytm wyznaczania wartości skrótu.  
  
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
  
 Element oidEntry > zawiera dwa atrybuty. [ \<](./file-schema/cryptography/oidentry-element.md) Atrybut **OID** jest numerem identyfikatora obiektu. Atrybut **name** jest wartością [ \<](./file-schema/cryptography/nameentry-element.md)atrybutu **name** z elementu nameEntry >. Aby można było zamapować identyfikator obiektu na prostą nazwę, musi istnieć mapowanie z nazwy algorytmu na klasę.  
  
## <a name="see-also"></a>Zobacz także

- [Konfigurowanie klas kryptografii](configure-cryptography-classes.md)
- [Usługi kryptograficzne](../../standard/security/cryptographic-services.md)
