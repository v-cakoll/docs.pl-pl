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
ms.openlocfilehash: 000d5d94b19907dfed40ac03f3172b9b8449c6f2
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083457"
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a>Mapowanie identyfikatorów obiektów na algorytmy kryptografii
Podpisy cyfrowe upewnij się, że dane nie zostanie naruszony po wysłaniu pomiędzy programami do innego. Zazwyczaj podpis cyfrowy jest obliczana przez zastosowanie funkcji matematycznych do wyznaczania wartości skrótu danych były podpisane. Podczas formatowania wartości skrótu, były podpisane, niektóre algorytmy podpisu cyfrowego Dołącz ASN.1 identyfikatora obiektu (OID) jako część operacji formatowania. OID Określa algorytm, który został użyty do obliczania skrótu. Algorytmy można zamapować na identyfikatory obiektów do rozszerzania mechanizmu szyfrowania do użycia algorytmów niestandardowych. Poniższy przykład pokazuje, jak zamapować nowy algorytm wyznaczania wartości skrótu identyfikatora obiektu.  
  
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
  
 [ \<Oidentry — > element](../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md) zawiera dwa atrybuty. **OID** atrybut jest numer identyfikatora obiektu. **Nazwa** atrybut jest wartość **nazwa** atrybut z [ \<nameentry — > element](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md). Musi istnieć mapowanie nazwy algorytmu na klasę, zanim identyfikator obiektu można zamapować prostą nazwą.  
  
## <a name="see-also"></a>Zobacz także
- [Konfigurowanie klas kryptografii](../../../docs/framework/configure-apps/configure-cryptography-classes.md)
- [Usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md)
