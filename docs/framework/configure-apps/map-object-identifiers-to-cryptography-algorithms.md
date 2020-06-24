---
title: Mapowanie identyfikatorów obiektów na algorytmy kryptografii
description: Zobacz jak zmapować identyfikator obiektu (OID) na algorytm kryptografii w programie .NET przy użyciu elementów oidEntry i nameEntry w pliku konfiguracyjnym XML.
ms.date: 03/30/2017
helpviewer_keywords:
- digital signatures
- identifiers, mapping object identifiers
- cryptographic algorithms
- mapping object identifiers
- cryptography, mapping object identifiers
ms.assetid: c9673f81-bf9e-47fd-bc6f-6bc1c1c4c15e
ms.openlocfilehash: e22510014071455b83ba28cd82690b5ecdce9bc9
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2020
ms.locfileid: "85142007"
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
  
 [ \<oidEntry> Element](./file-schema/cryptography/oidentry-element.md) zawiera dwa atrybuty. Atrybut **OID** jest numerem identyfikatora obiektu. Atrybut **name** jest wartością atrybutu **name** z [ \<nameEntry> elementu](./file-schema/cryptography/nameentry-element.md). Aby można było zamapować identyfikator obiektu na prostą nazwę, musi istnieć mapowanie z nazwy algorytmu na klasę.  
  
## <a name="see-also"></a>Zobacz też

- [Konfigurowanie klasy kryptografii](configure-cryptography-classes.md)
- [Usługi kryptograficzne](../../standard/security/cryptographic-services.md)
