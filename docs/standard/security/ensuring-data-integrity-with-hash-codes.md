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
ms.openlocfilehash: 16770ea938973372d1d94c628c42d5d5bf10c695
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43874995"
---
# <a name="ensuring-data-integrity-with-hash-codes"></a><span data-ttu-id="8ba4e-102">Zapewnianie integralności danych za pomocą wartości skrótu</span><span class="sxs-lookup"><span data-stu-id="8ba4e-102">Ensuring Data Integrity with Hash Codes</span></span>
<span data-ttu-id="8ba4e-103">Wartość skrótu jest wartością liczbową o stałej długości, która jednoznacznie identyfikuje dane.</span><span class="sxs-lookup"><span data-stu-id="8ba4e-103">A hash value is a numeric value of a fixed length that uniquely identifies data.</span></span> <span data-ttu-id="8ba4e-104">Wartości skrótów reprezentują dużych ilości danych jako dużo mniejsze wartości liczbowe, dzięki czemu są one używane, za pomocą podpisów cyfrowych.</span><span class="sxs-lookup"><span data-stu-id="8ba4e-104">Hash values represent large amounts of data as much smaller numeric values, so they are used with digital signatures.</span></span> <span data-ttu-id="8ba4e-105">Wartość skrótu można podpisać efektywniej niż podpisywania większa wartość.</span><span class="sxs-lookup"><span data-stu-id="8ba4e-105">You can sign a hash value more efficiently than signing the larger value.</span></span> <span data-ttu-id="8ba4e-106">Wartości skrótu są również przydatne w przypadku sprawdzania integralności danych przesyłanych za pośrednictwem niezabezpieczonych kanałów.</span><span class="sxs-lookup"><span data-stu-id="8ba4e-106">Hash values are also useful for verifying the integrity of data sent through insecure channels.</span></span> <span data-ttu-id="8ba4e-107">Wartość skrótu odebranych danych można porównać do wartości skrótu danych jako wysłano w celu ustalenia, czy dane zostało zmienione.</span><span class="sxs-lookup"><span data-stu-id="8ba4e-107">The hash value of received data can be compared to the hash value of data as it was sent to determine whether the data was altered.</span></span>  
  
 <span data-ttu-id="8ba4e-108">W tym temacie opisano sposób generowania i sprawdzić kody skrótów przy użyciu klas w <xref:System.Security.Cryptography?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="8ba4e-108">This topic describes how to generate and verify hash codes by using the classes in the <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="generating-a-hash"></a><span data-ttu-id="8ba4e-109">Generowanie skrótów</span><span class="sxs-lookup"><span data-stu-id="8ba4e-109">Generating a Hash</span></span>  
 <span data-ttu-id="8ba4e-110">Klasy zarządzane wyznaczania wartości skrótu można skrótu tablicę bajtów lub obiektu zarządzanego strumienia.</span><span class="sxs-lookup"><span data-stu-id="8ba4e-110">The managed hash classes can hash either an array of bytes or a managed stream object.</span></span> <span data-ttu-id="8ba4e-111">W poniższym przykładzie użyto algorytmu wyznaczania wartości skrótu SHA1, aby utworzyć wartość skrótu ciągu.</span><span class="sxs-lookup"><span data-stu-id="8ba4e-111">The following example uses the SHA1 hash algorithm to create a hash value for a string.</span></span> <span data-ttu-id="8ba4e-112">W przykładzie użyto <xref:System.Text.UnicodeEncoding> klasy w celu przekonwertowania ciągu na tablicę bajtów, które są przekazywane przy użyciu <xref:System.Security.Cryptography.SHA1Managed> klasy.</span><span class="sxs-lookup"><span data-stu-id="8ba4e-112">The example uses the <xref:System.Text.UnicodeEncoding> class to convert the string into an array of bytes that are hashed by using the <xref:System.Security.Cryptography.SHA1Managed> class.</span></span> <span data-ttu-id="8ba4e-113">Wartość skrótu jest następnie wyświetlana w konsoli.</span><span class="sxs-lookup"><span data-stu-id="8ba4e-113">The hash value is then displayed to the console.</span></span>  
  
 [!code-csharp[GeneratingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/generatingahash/cs/program.cs#1)]
 [!code-vb[GeneratingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/generatingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="8ba4e-114">Ten kod wyświetli następujący ciąg do konsoli:</span><span class="sxs-lookup"><span data-stu-id="8ba4e-114">This code will display the following string to the console:</span></span>  
  
 `59 4 248 102 77 97 142 201 210 12 224 93 25 41 100 197 213 134 130 135`  
  
## <a name="verifying-a-hash"></a><span data-ttu-id="8ba4e-115">Weryfikowanie wartości skrótu</span><span class="sxs-lookup"><span data-stu-id="8ba4e-115">Verifying a Hash</span></span>  
 <span data-ttu-id="8ba4e-116">Dane można porównać do wartość skrótu, aby określić ich integralności.</span><span class="sxs-lookup"><span data-stu-id="8ba4e-116">Data can be compared to a hash value to determine its integrity.</span></span> <span data-ttu-id="8ba4e-117">Zazwyczaj danych jest wyznaczana wartość skrótu w określonym czasie, a wartość skrótu jest chroniona w jakiś sposób.</span><span class="sxs-lookup"><span data-stu-id="8ba4e-117">Usually, data is hashed at a certain time and the hash value is protected in some way.</span></span> <span data-ttu-id="8ba4e-118">W późniejszym czasie dane można ponownie skrótu i porównywana z wartością chronionych.</span><span class="sxs-lookup"><span data-stu-id="8ba4e-118">At a later time, the data can be hashed again and compared to the protected value.</span></span> <span data-ttu-id="8ba4e-119">Jeśli wartości skrótu są zgodne, dane nie został zmieniony.</span><span class="sxs-lookup"><span data-stu-id="8ba4e-119">If the hash values match, the data has not been altered.</span></span> <span data-ttu-id="8ba4e-120">Jeśli wartości nie są zgodne, zostały uszkodzone dane.</span><span class="sxs-lookup"><span data-stu-id="8ba4e-120">If the values do not match, the data has been corrupted.</span></span> <span data-ttu-id="8ba4e-121">Dla tego systemu do pracy chronionych skrótu musi być szyfrowane lub trzymane w tajemnicy wszystkie niezaufane.</span><span class="sxs-lookup"><span data-stu-id="8ba4e-121">For this system to work, the protected hash must be encrypted or kept secret from all untrusted parties.</span></span>  
  
 <span data-ttu-id="8ba4e-122">W poniższym przykładzie porównano poprzednią wartość skrótu ciągu na nową wartość skrótu.</span><span class="sxs-lookup"><span data-stu-id="8ba4e-122">The following example compares the previous hash value of a string to a new hash value.</span></span> <span data-ttu-id="8ba4e-123">W tym przykładzie pętli poszczególne bajty wartości skrótu i sprawia, że porównanie.</span><span class="sxs-lookup"><span data-stu-id="8ba4e-123">This example loops through each byte of the hash values and makes a comparison.</span></span>  
  
 [!code-csharp[VerifyingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/verifyingahash/cs/program.cs#1)]
 [!code-vb[VerifyingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/verifyingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="8ba4e-124">Jeśli wartości skrótu dwóch zgodne, ten kod wyświetla następujące do konsoli:</span><span class="sxs-lookup"><span data-stu-id="8ba4e-124">If the two hash values match, this code displays the following to the console:</span></span>  
  
```  
The hash codes match.  
```  
  
 <span data-ttu-id="8ba4e-125">Jeśli nie są zgodne, ten kod wyświetla następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="8ba4e-125">If they do not match, the code displays the following:</span></span>  
  
```  
The hash codes do not match.  
```  
  
## <a name="see-also"></a><span data-ttu-id="8ba4e-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ba4e-126">See also</span></span>

- [<span data-ttu-id="8ba4e-127">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="8ba4e-127">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
