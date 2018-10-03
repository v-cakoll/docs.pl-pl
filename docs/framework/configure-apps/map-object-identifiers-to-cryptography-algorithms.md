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
ms.openlocfilehash: d23fc48a53ee47aacfc290b52887b800ce37477f
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48036862"
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a><span data-ttu-id="e03ac-102">Mapowanie identyfikatorów obiektów na algorytmy kryptografii</span><span class="sxs-lookup"><span data-stu-id="e03ac-102">Mapping Object Identifiers to Cryptography Algorithms</span></span>
<span data-ttu-id="e03ac-103">Podpisy cyfrowe upewnij się, że dane nie zostanie naruszony po wysłaniu pomiędzy programami do innego.</span><span class="sxs-lookup"><span data-stu-id="e03ac-103">Digital signatures ensure that data is not tampered with when it is sent from one program to another.</span></span> <span data-ttu-id="e03ac-104">Zazwyczaj podpis cyfrowy jest obliczana przez zastosowanie funkcji matematycznych do wyznaczania wartości skrótu danych były podpisane.</span><span class="sxs-lookup"><span data-stu-id="e03ac-104">Typically the digital signature is computed by applying a mathematical function to the hash of the data to be signed.</span></span> <span data-ttu-id="e03ac-105">Podczas formatowania wartości skrótu, były podpisane, niektóre algorytmy podpisu cyfrowego Dołącz ASN.1 identyfikatora obiektu (OID) jako część operacji formatowania.</span><span class="sxs-lookup"><span data-stu-id="e03ac-105">When formatting a hash value to be signed, some digital signature algorithms append an ASN.1 Object Identifier (OID) as part of the formatting operation.</span></span> <span data-ttu-id="e03ac-106">OID Określa algorytm, który został użyty do obliczania skrótu.</span><span class="sxs-lookup"><span data-stu-id="e03ac-106">The OID identifies the algorithm that was used to compute the hash.</span></span> <span data-ttu-id="e03ac-107">Algorytmy można zamapować na identyfikatory obiektów do rozszerzania mechanizmu szyfrowania do użycia algorytmów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="e03ac-107">You can map algorithms to object identifiers to extend the cryptography mechanism to use custom algorithms.</span></span> <span data-ttu-id="e03ac-108">Poniższy przykład pokazuje, jak zamapować nowy algorytm wyznaczania wartości skrótu identyfikatora obiektu.</span><span class="sxs-lookup"><span data-stu-id="e03ac-108">The following example shows how to map an object identifier to a new hash algorithm.</span></span>  
  
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
  
 <span data-ttu-id="e03ac-109">[ \<Oidentry — > element](../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md) zawiera dwa atrybuty.</span><span class="sxs-lookup"><span data-stu-id="e03ac-109">The [\<oidEntry> element](../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md) contains two attributes.</span></span> <span data-ttu-id="e03ac-110">**OID** atrybut jest numer identyfikatora obiektu.</span><span class="sxs-lookup"><span data-stu-id="e03ac-110">The **OID** attribute is the object identifier number.</span></span> <span data-ttu-id="e03ac-111">**Nazwa** atrybut jest wartość **nazwa** atrybut z [ \<nameentry — > element](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md).</span><span class="sxs-lookup"><span data-stu-id="e03ac-111">The **name** attribute is the value of the **name** attribute from the [\<nameEntry> element](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md).</span></span> <span data-ttu-id="e03ac-112">Musi istnieć mapowanie nazwy algorytmu na klasę, zanim identyfikator obiektu można zamapować prostą nazwą.</span><span class="sxs-lookup"><span data-stu-id="e03ac-112">There must be a mapping from an algorithm name to a class before an object identifier can be mapped to a simple name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e03ac-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e03ac-113">See Also</span></span>  
 [<span data-ttu-id="e03ac-114">Konfigurowanie klas kryptografii</span><span class="sxs-lookup"><span data-stu-id="e03ac-114">Configuring Cryptography Classes</span></span>](../../../docs/framework/configure-apps/configure-cryptography-classes.md)  
 [<span data-ttu-id="e03ac-115">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="e03ac-115">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
