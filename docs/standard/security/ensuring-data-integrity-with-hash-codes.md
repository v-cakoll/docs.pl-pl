---
title: Zapewnianie integralności danych za pomocą wartości skrótu
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 995f54e81a48fb3f809d99981ad135974544eb28
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353171"
---
# <a name="ensuring-data-integrity-with-hash-codes"></a><span data-ttu-id="2b505-102">Zapewnianie integralności danych za pomocą wartości skrótu</span><span class="sxs-lookup"><span data-stu-id="2b505-102">Ensuring Data Integrity with Hash Codes</span></span>
<span data-ttu-id="2b505-103">Wartość skrótu to wartość liczbowa o stałej długości, która jednoznacznie identyfikuje dane.</span><span class="sxs-lookup"><span data-stu-id="2b505-103">A hash value is a numeric value of a fixed length that uniquely identifies data.</span></span> <span data-ttu-id="2b505-104">Wartości skrótu przedstawiają duże ilości danych jako dużo mniejsze wartości liczbowe, dlatego są używane z podpisami cyfrowymi.</span><span class="sxs-lookup"><span data-stu-id="2b505-104">Hash values represent large amounts of data as much smaller numeric values, so they are used with digital signatures.</span></span> <span data-ttu-id="2b505-105">Wartość skrótu można podpisywać bardziej wydajnie niż podpisywanie większej wartości.</span><span class="sxs-lookup"><span data-stu-id="2b505-105">You can sign a hash value more efficiently than signing the larger value.</span></span> <span data-ttu-id="2b505-106">Wartości skrótu są również przydatne do sprawdzania integralności danych wysyłanych za pomocą niezabezpieczonych kanałów.</span><span class="sxs-lookup"><span data-stu-id="2b505-106">Hash values are also useful for verifying the integrity of data sent through insecure channels.</span></span> <span data-ttu-id="2b505-107">Wartość skrótu odebranych danych może być porównywana z wartością skrótu danych, która została wysłana w celu określenia, czy dane zostały zmienione.</span><span class="sxs-lookup"><span data-stu-id="2b505-107">The hash value of received data can be compared to the hash value of data as it was sent to determine whether the data was altered.</span></span>  
  
 <span data-ttu-id="2b505-108">W tym temacie opisano sposób generowania i weryfikowania kodów skrótów przy użyciu klas w <xref:System.Security.Cryptography?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2b505-108">This topic describes how to generate and verify hash codes by using the classes in the <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="generating-a-hash"></a><span data-ttu-id="2b505-109">Generowanie skrótu</span><span class="sxs-lookup"><span data-stu-id="2b505-109">Generating a Hash</span></span>  
 <span data-ttu-id="2b505-110">Zarządzane klasy skrótów mogą mieszać tablicę bajtów lub obiekt strumienia zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="2b505-110">The managed hash classes can hash either an array of bytes or a managed stream object.</span></span> <span data-ttu-id="2b505-111">W poniższym przykładzie jest używany algorytm skrótu SHA1 do tworzenia wartości skrótu dla ciągu.</span><span class="sxs-lookup"><span data-stu-id="2b505-111">The following example uses the SHA1 hash algorithm to create a hash value for a string.</span></span> <span data-ttu-id="2b505-112">W przykładzie użyto <xref:System.Text.UnicodeEncoding> klasy do przekonwertowania ciągu na tablicę bajtów, które są zmieszane przy <xref:System.Security.Cryptography.SHA1Managed> użyciu klasy.</span><span class="sxs-lookup"><span data-stu-id="2b505-112">The example uses the <xref:System.Text.UnicodeEncoding> class to convert the string into an array of bytes that are hashed by using the <xref:System.Security.Cryptography.SHA1Managed> class.</span></span> <span data-ttu-id="2b505-113">Wartość skrótu zostanie następnie wyświetlona w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="2b505-113">The hash value is then displayed to the console.</span></span>  

 <span data-ttu-id="2b505-114">Ze względu na kolizje problemów z algorytmem SHA1 firma Microsoft zaleca SHA256ą lub lepszą.</span><span class="sxs-lookup"><span data-stu-id="2b505-114">Due to collision problems with SHA1, Microsoft recommends SHA256 or better.</span></span>
  
 [!code-csharp[GeneratingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/generatingahash/cs/program.cs#1)]
 [!code-vb[GeneratingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/generatingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="2b505-115">Ten kod będzie wyświetlał następujący ciąg do konsoli:</span><span class="sxs-lookup"><span data-stu-id="2b505-115">This code will display the following string to the console:</span></span>  
  
 `59 4 248 102 77 97 142 201 210 12 224 93 25 41 100 197 213 134 130 135`  
  
## <a name="verifying-a-hash"></a><span data-ttu-id="2b505-116">Weryfikowanie skrótu</span><span class="sxs-lookup"><span data-stu-id="2b505-116">Verifying a Hash</span></span>  
 <span data-ttu-id="2b505-117">Dane można porównać do wartości skrótu, aby określić jej integralność.</span><span class="sxs-lookup"><span data-stu-id="2b505-117">Data can be compared to a hash value to determine its integrity.</span></span> <span data-ttu-id="2b505-118">Zwykle dane są zmieszane w określonym czasie, a wartość skrótu jest chroniona w jakiś sposób.</span><span class="sxs-lookup"><span data-stu-id="2b505-118">Usually, data is hashed at a certain time and the hash value is protected in some way.</span></span> <span data-ttu-id="2b505-119">Później można ponownie wykonać mieszanie danych i porównywać ją z wartością chronioną.</span><span class="sxs-lookup"><span data-stu-id="2b505-119">At a later time, the data can be hashed again and compared to the protected value.</span></span> <span data-ttu-id="2b505-120">W przypadku dopasowania wartości skrótu dane nie zostały zmienione.</span><span class="sxs-lookup"><span data-stu-id="2b505-120">If the hash values match, the data has not been altered.</span></span> <span data-ttu-id="2b505-121">Jeśli wartości nie są zgodne, dane zostały uszkodzone.</span><span class="sxs-lookup"><span data-stu-id="2b505-121">If the values do not match, the data has been corrupted.</span></span> <span data-ttu-id="2b505-122">Aby ten system działał, chroniony skrót musi być zaszyfrowany lub przechowywany jako wpis tajny ze wszystkich niezaufanych stron.</span><span class="sxs-lookup"><span data-stu-id="2b505-122">For this system to work, the protected hash must be encrypted or kept secret from all untrusted parties.</span></span>  
  
 <span data-ttu-id="2b505-123">Poniższy przykład porównuje poprzednią wartość skrótu ciągu z nową wartością skrótu.</span><span class="sxs-lookup"><span data-stu-id="2b505-123">The following example compares the previous hash value of a string to a new hash value.</span></span> <span data-ttu-id="2b505-124">Ten przykład powoduje pętlę przez każdy bajt wartości skrótu i wykonuje porównanie.</span><span class="sxs-lookup"><span data-stu-id="2b505-124">This example loops through each byte of the hash values and makes a comparison.</span></span>  
  
 [!code-csharp[VerifyingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/verifyingahash/cs/program.cs#1)]
 [!code-vb[VerifyingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/verifyingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="2b505-125">Jeśli dwie wartości skrótów są zgodne, ten kod wyświetla następujące polecenie w konsoli programu:</span><span class="sxs-lookup"><span data-stu-id="2b505-125">If the two hash values match, this code displays the following to the console:</span></span>  
  
```console  
The hash codes match.  
```  
  
 <span data-ttu-id="2b505-126">Jeśli nie są zgodne, kod wyświetla następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="2b505-126">If they do not match, the code displays the following:</span></span>  
  
```console  
The hash codes do not match.  
```  
  
## <a name="see-also"></a><span data-ttu-id="2b505-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2b505-127">See also</span></span>

- [<span data-ttu-id="2b505-128">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="2b505-128">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
