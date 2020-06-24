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
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a><span data-ttu-id="08354-103">Mapowanie identyfikatorów obiektów na algorytmy kryptografii</span><span class="sxs-lookup"><span data-stu-id="08354-103">Mapping Object Identifiers to Cryptography Algorithms</span></span>
<span data-ttu-id="08354-104">Podpisy cyfrowe zapewniają, że dane nie są modyfikowane, gdy są wysyłane z jednego programu do drugiego.</span><span class="sxs-lookup"><span data-stu-id="08354-104">Digital signatures ensure that data is not tampered with when it is sent from one program to another.</span></span> <span data-ttu-id="08354-105">Zwykle podpis cyfrowy jest obliczany przez zastosowanie funkcji matematycznej do skrótu danych do podpisania.</span><span class="sxs-lookup"><span data-stu-id="08354-105">Typically the digital signature is computed by applying a mathematical function to the hash of the data to be signed.</span></span> <span data-ttu-id="08354-106">Podczas formatowania wartości skrótu do podpisania niektóre algorytmy podpisu cyfrowego dołączają identyfikator (OID) ASN. 1 jako część operacji formatowania.</span><span class="sxs-lookup"><span data-stu-id="08354-106">When formatting a hash value to be signed, some digital signature algorithms append an ASN.1 Object Identifier (OID) as part of the formatting operation.</span></span> <span data-ttu-id="08354-107">Identyfikator OID identyfikuje algorytm używany do obliczania skrótu.</span><span class="sxs-lookup"><span data-stu-id="08354-107">The OID identifies the algorithm that was used to compute the hash.</span></span> <span data-ttu-id="08354-108">Można mapować algorytmy do identyfikatorów obiektów, aby zwiększyć mechanizm kryptografii do korzystania z algorytmów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="08354-108">You can map algorithms to object identifiers to extend the cryptography mechanism to use custom algorithms.</span></span> <span data-ttu-id="08354-109">Poniższy przykład przedstawia sposób mapowania identyfikatora obiektu na nowy algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="08354-109">The following example shows how to map an object identifier to a new hash algorithm.</span></span>  
  
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
  
 <span data-ttu-id="08354-110">[ \<oidEntry> Element](./file-schema/cryptography/oidentry-element.md) zawiera dwa atrybuty.</span><span class="sxs-lookup"><span data-stu-id="08354-110">The [\<oidEntry> element](./file-schema/cryptography/oidentry-element.md) contains two attributes.</span></span> <span data-ttu-id="08354-111">Atrybut **OID** jest numerem identyfikatora obiektu.</span><span class="sxs-lookup"><span data-stu-id="08354-111">The **OID** attribute is the object identifier number.</span></span> <span data-ttu-id="08354-112">Atrybut **name** jest wartością atrybutu **name** z [ \<nameEntry> elementu](./file-schema/cryptography/nameentry-element.md).</span><span class="sxs-lookup"><span data-stu-id="08354-112">The **name** attribute is the value of the **name** attribute from the [\<nameEntry> element](./file-schema/cryptography/nameentry-element.md).</span></span> <span data-ttu-id="08354-113">Aby można było zamapować identyfikator obiektu na prostą nazwę, musi istnieć mapowanie z nazwy algorytmu na klasę.</span><span class="sxs-lookup"><span data-stu-id="08354-113">There must be a mapping from an algorithm name to a class before an object identifier can be mapped to a simple name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08354-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="08354-114">See also</span></span>

- [<span data-ttu-id="08354-115">Konfigurowanie klasy kryptografii</span><span class="sxs-lookup"><span data-stu-id="08354-115">Configuring Cryptography Classes</span></span>](configure-cryptography-classes.md)
- [<span data-ttu-id="08354-116">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="08354-116">Cryptographic Services</span></span>](../../standard/security/cryptographic-services.md)
