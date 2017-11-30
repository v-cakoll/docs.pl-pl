---
title: "Zapewnianie integralności danych za pomocą wartości skrótu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- generating hash
- verifying hash codes
- cryptography [.NET Framework], hash
- data integrity
- checking hash codes
- encryption [.NET Framework], hash
- hash
ms.assetid: 33660f33-b70f-4dca-8c87-ab35cfc2961a
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b5d54a608ae87a1b453b4fa2b4b351ac5fc9f068
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ensuring-data-integrity-with-hash-codes"></a><span data-ttu-id="19a20-102">Zapewnianie integralności danych za pomocą wartości skrótu</span><span class="sxs-lookup"><span data-stu-id="19a20-102">Ensuring Data Integrity with Hash Codes</span></span>
<span data-ttu-id="19a20-103">Wartość skrótu jest wartość liczbową o stałej długości, który unikatowo identyfikuje dane.</span><span class="sxs-lookup"><span data-stu-id="19a20-103">A hash value is a numeric value of a fixed length that uniquely identifies data.</span></span> <span data-ttu-id="19a20-104">Wartości skrótu reprezentują dużych ilości danych jako dużo mniejsze wartości liczbowe, dlatego są one używane z podpisami cyfrowymi.</span><span class="sxs-lookup"><span data-stu-id="19a20-104">Hash values represent large amounts of data as much smaller numeric values, so they are used with digital signatures.</span></span> <span data-ttu-id="19a20-105">Wartość skrótu można podpisać efektywniej niż podpisywania wyższej wartości.</span><span class="sxs-lookup"><span data-stu-id="19a20-105">You can sign a hash value more efficiently than signing the larger value.</span></span> <span data-ttu-id="19a20-106">Wartości skrótu są także przydatne do sprawdzania integralności danych przesyłanych za pośrednictwem niezabezpieczonych kanałów.</span><span class="sxs-lookup"><span data-stu-id="19a20-106">Hash values are also useful for verifying the integrity of data sent through insecure channels.</span></span> <span data-ttu-id="19a20-107">Wartość skrótu odebranych danych można porównać wartości skrótu danych jako został wysłany do określenia, czy dane zostało zmienione.</span><span class="sxs-lookup"><span data-stu-id="19a20-107">The hash value of received data can be compared to the hash value of data as it was sent to determine whether the data was altered.</span></span>  
  
 <span data-ttu-id="19a20-108">W tym temacie opisano sposób generować i weryfikować skrótu przy użyciu klasy w <xref:System.Security.Cryptography?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="19a20-108">This topic describes how to generate and verify hash codes by using the classes in the <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="generating-a-hash"></a><span data-ttu-id="19a20-109">Generowanie skrótów</span><span class="sxs-lookup"><span data-stu-id="19a20-109">Generating a Hash</span></span>  
 <span data-ttu-id="19a20-110">Klasy zarządzane wyznaczania wartości skrótu można skrótu tablicę bajtów lub obiektu zarządzanego strumienia.</span><span class="sxs-lookup"><span data-stu-id="19a20-110">The managed hash classes can hash either an array of bytes or a managed stream object.</span></span> <span data-ttu-id="19a20-111">W poniższym przykładzie użyto algorytmu wyznaczania wartości skrótu SHA1, aby utworzyć wartość skrótu ciągu.</span><span class="sxs-lookup"><span data-stu-id="19a20-111">The following example uses the SHA1 hash algorithm to create a hash value for a string.</span></span> <span data-ttu-id="19a20-112">W przykładzie użyto <xref:System.Text.UnicodeEncoding> klasę, aby przekonwertować ciąg na tablicę bajtów, które są przechowywane w formie skrótu, za pomocą <xref:System.Security.Cryptography.SHA1Managed> klasy.</span><span class="sxs-lookup"><span data-stu-id="19a20-112">The example uses the <xref:System.Text.UnicodeEncoding> class to convert the string into an array of bytes that are hashed by using the <xref:System.Security.Cryptography.SHA1Managed> class.</span></span> <span data-ttu-id="19a20-113">Wartość skrótu jest następnie wyświetlane w konsoli.</span><span class="sxs-lookup"><span data-stu-id="19a20-113">The hash value is then displayed to the console.</span></span>  
  
 [!code-csharp[GeneratingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/generatingahash/cs/program.cs#1)]
 [!code-vb[GeneratingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/generatingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="19a20-114">Ten kod wyświetli następujący ciąg do konsoli:</span><span class="sxs-lookup"><span data-stu-id="19a20-114">This code will display the following string to the console:</span></span>  
  
 `59 4 248 102 77 97 142 201 210 12 224 93 25 41 100 197 213 134 130 135`  
  
## <a name="verifying-a-hash"></a><span data-ttu-id="19a20-115">Sprawdzanie wartości skrótu</span><span class="sxs-lookup"><span data-stu-id="19a20-115">Verifying a Hash</span></span>  
 <span data-ttu-id="19a20-116">Dane mogą być porównywane do wartości skrótu, aby ustalić jego integralności.</span><span class="sxs-lookup"><span data-stu-id="19a20-116">Data can be compared to a hash value to determine its integrity.</span></span> <span data-ttu-id="19a20-117">Zazwyczaj jest przemieszać danych w określonym czasie i wartości skrótu jest chroniona w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="19a20-117">Usually, data is hashed at a certain time and the hash value is protected in some way.</span></span> <span data-ttu-id="19a20-118">W późniejszym czasie dane można ponownie mieszany i porównywana z wartością chronionych.</span><span class="sxs-lookup"><span data-stu-id="19a20-118">At a later time, the data can be hashed again and compared to the protected value.</span></span> <span data-ttu-id="19a20-119">Jeśli wartości skrótu są zgodne, dane nie zostały zmienione.</span><span class="sxs-lookup"><span data-stu-id="19a20-119">If the hash values match, the data has not been altered.</span></span> <span data-ttu-id="19a20-120">Jeśli wartości nie są zgodne, danych została uszkodzona.</span><span class="sxs-lookup"><span data-stu-id="19a20-120">If the values do not match, the data has been corrupted.</span></span> <span data-ttu-id="19a20-121">Dla tego systemu do pracy chronionych skrót musi być szyfrowane lub ujawniana wszystkie niezaufane.</span><span class="sxs-lookup"><span data-stu-id="19a20-121">For this system to work, the protected hash must be encrypted or kept secret from all untrusted parties.</span></span>  
  
 <span data-ttu-id="19a20-122">Poniższy przykład porównuje Poprzednia wartość skrótu ciągu na nową wartość skrótu.</span><span class="sxs-lookup"><span data-stu-id="19a20-122">The following example compares the previous hash value of a string to a new hash value.</span></span> <span data-ttu-id="19a20-123">W tym przykładzie każdy bajt wartości skrótu w pętli i sprawia, że porównanie.</span><span class="sxs-lookup"><span data-stu-id="19a20-123">This example loops through each byte of the hash values and makes a comparison.</span></span>  
  
 [!code-csharp[VerifyingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/verifyingahash/cs/program.cs#1)]
 [!code-vb[VerifyingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/verifyingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="19a20-124">Jeśli wartości skrótu dwóch zgodne, ten kod wyświetla następujące do konsoli:</span><span class="sxs-lookup"><span data-stu-id="19a20-124">If the two hash values match, this code displays the following to the console:</span></span>  
  
```  
The hash codes match.  
```  
  
 <span data-ttu-id="19a20-125">Jeśli nie są zgodne, kod wyświetla następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="19a20-125">If they do not match, the code displays the following:</span></span>  
  
```  
The hash codes do not match.  
```  
  
## <a name="see-also"></a><span data-ttu-id="19a20-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="19a20-126">See Also</span></span>  
 [<span data-ttu-id="19a20-127">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="19a20-127">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
