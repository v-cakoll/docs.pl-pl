---
title: 'Porady: stosowanie ochrony danych'
description: Dowiedz się, jak używać ochrony danych, uzyskując dostęp do interfejsu API ochrony danych (DPAPI) w środowisku .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DPAPI
- encryption [.NET Framework], data protection API
- data [.NET Framework], decryption
- ProtectedMemory class, about ProtectedMemory class
- ProtectedData class, about ProtectedData class
- cryptography [.NET Framework], data protection API
- data protection API [.NET Framework]
- decryption
- data [.NET Framework], encryption
ms.assetid: 606698b0-cb1a-42ca-beeb-0bea34205d20
ms.openlocfilehash: c7f88105727dfd33c87a815054aa317ac2052e83
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598596"
---
# <a name="how-to-use-data-protection"></a><span data-ttu-id="be601-103">Porady: stosowanie ochrony danych</span><span class="sxs-lookup"><span data-stu-id="be601-103">How to: Use Data Protection</span></span>
<span data-ttu-id="be601-104">.NET Framework zapewnia dostęp do interfejsu API ochrony danych (DPAPI), który umożliwia szyfrowanie danych przy użyciu informacji z bieżącego konta użytkownika lub komputera.</span><span class="sxs-lookup"><span data-stu-id="be601-104">The .NET Framework provides access to the data protection API (DPAPI), which allows you to encrypt data using information from the current user account or computer.</span></span>  <span data-ttu-id="be601-105">Korzystając z interfejsu DPAPI, można złagodzić trudne problemy związane z jawnym generowaniem i przechowywaniem klucza kryptograficznego.</span><span class="sxs-lookup"><span data-stu-id="be601-105">When you use the DPAPI, you alleviate the difficult problem of explicitly generating and storing a cryptographic key.</span></span>  
  
 <span data-ttu-id="be601-106">Użyj <xref:System.Security.Cryptography.ProtectedMemory> klasy, aby zaszyfrować tablicę bajtów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="be601-106">Use the <xref:System.Security.Cryptography.ProtectedMemory> class to encrypt an array of in-memory bytes.</span></span>  <span data-ttu-id="be601-107">Ta funkcja jest dostępna w systemie Microsoft Windows XP i nowszych systemach operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="be601-107">This functionality is available in Microsoft Windows XP and later operating systems.</span></span>  <span data-ttu-id="be601-108">Można określić, że pamięć zaszyfrowana przez bieżący proces może zostać odszyfrowana tylko przez bieżący proces, przez wszystkie procesy lub z tego samego kontekstu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="be601-108">You can specify that memory encrypted by the current process can be decrypted by the current process only, by all processes, or from the same user context.</span></span>  <span data-ttu-id="be601-109"><xref:System.Security.Cryptography.MemoryProtectionScope>Szczegółowy opis opcji można znaleźć w wyliczeniu <xref:System.Security.Cryptography.ProtectedMemory> .</span><span class="sxs-lookup"><span data-stu-id="be601-109">See the <xref:System.Security.Cryptography.MemoryProtectionScope> enumeration for a detailed description of <xref:System.Security.Cryptography.ProtectedMemory> options.</span></span>  
  
 <span data-ttu-id="be601-110">Użyj <xref:System.Security.Cryptography.ProtectedData> klasy, aby zaszyfrować kopię tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="be601-110">Use the <xref:System.Security.Cryptography.ProtectedData> class to encrypt a copy of an array of bytes.</span></span> <span data-ttu-id="be601-111">Ta funkcja jest dostępna w systemie Microsoft Windows 2000 i nowszych systemach operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="be601-111">This functionality is available in Microsoft Windows 2000 and later operating systems.</span></span>  <span data-ttu-id="be601-112">Możesz określić, że dane zaszyfrowane przez bieżące konto użytkownika mogą zostać odszyfrowane tylko przez to samo konto użytkownika, lub możesz określić, że dane zaszyfrowane przez bieżące konto użytkownika mogą zostać odszyfrowane za pomocą dowolnego konta na komputerze.</span><span class="sxs-lookup"><span data-stu-id="be601-112">You can specify that data encrypted by the current user account can be decrypted only by the same user account, or you can specify that data encrypted by the current user account can be decrypted by any account on the computer.</span></span>  <span data-ttu-id="be601-113"><xref:System.Security.Cryptography.DataProtectionScope>Szczegółowy opis opcji można znaleźć w wyliczeniu <xref:System.Security.Cryptography.ProtectedData> .</span><span class="sxs-lookup"><span data-stu-id="be601-113">See the <xref:System.Security.Cryptography.DataProtectionScope> enumeration for a detailed description of <xref:System.Security.Cryptography.ProtectedData> options.</span></span>  
  
### <a name="to-encrypt-in-memory-data-using-data-protection"></a><span data-ttu-id="be601-114">Aby zaszyfrować dane znajdujące się w pamięci przy użyciu ochrony danych</span><span class="sxs-lookup"><span data-stu-id="be601-114">To encrypt in-memory data using data protection</span></span>  
  
1. <span data-ttu-id="be601-115">Wywołaj metodę statyczną <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> podczas przekazywania tablicy bajtów do szyfrowania, entropii i zakresu ochrony pamięci.</span><span class="sxs-lookup"><span data-stu-id="be601-115">Call the static <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> method while passing an array of bytes to encrypt, the entropy, and the memory protection scope.</span></span>  
  
### <a name="to-decrypt-in-memory-data-using-data-protection"></a><span data-ttu-id="be601-116">Aby odszyfrować dane w pamięci przy użyciu ochrony danych</span><span class="sxs-lookup"><span data-stu-id="be601-116">To decrypt in-memory data using data protection</span></span>  
  
1. <span data-ttu-id="be601-117">Wywołaj metodę statyczną <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> podczas przekazywania tablicy bajtów do odszyfrowania i zakresu ochrony pamięci.</span><span class="sxs-lookup"><span data-stu-id="be601-117">Call the static <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> method while passing an array of bytes to decrypt and the memory protection scope.</span></span>  
  
### <a name="to-encrypt-data-to-a-file-or-stream-using-data-protection"></a><span data-ttu-id="be601-118">Aby zaszyfrować dane do pliku lub strumienia przy użyciu ochrony danych</span><span class="sxs-lookup"><span data-stu-id="be601-118">To encrypt data to a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="be601-119">Utwórz entropię losową.</span><span class="sxs-lookup"><span data-stu-id="be601-119">Create random entropy.</span></span>  
  
2. <span data-ttu-id="be601-120">Wywołaj metodę statyczną <xref:System.Security.Cryptography.ProtectedData.Protect%2A> podczas przekazywania tablicy bajtów do szyfrowania, entropii i zakresu ochrony danych.</span><span class="sxs-lookup"><span data-stu-id="be601-120">Call the static <xref:System.Security.Cryptography.ProtectedData.Protect%2A> method while passing an array of bytes to encrypt, the entropy, and the data protection scope.</span></span>  
  
3. <span data-ttu-id="be601-121">Zapisz dane zaszyfrowane do pliku lub strumienia.</span><span class="sxs-lookup"><span data-stu-id="be601-121">Write the encrypted data to a file or stream.</span></span>  
  
### <a name="to-decrypt-data-from-a-file-or-stream-using-data-protection"></a><span data-ttu-id="be601-122">Aby odszyfrować dane z pliku lub strumienia przy użyciu ochrony danych</span><span class="sxs-lookup"><span data-stu-id="be601-122">To decrypt data from a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="be601-123">Odczytaj zaszyfrowane dane z pliku lub strumienia.</span><span class="sxs-lookup"><span data-stu-id="be601-123">Read the encrypted data from a file or stream.</span></span>  
  
2. <span data-ttu-id="be601-124">Wywołaj metodę statyczną <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> podczas przekazywania tablicy bajtów do odszyfrowania i zakresu ochrony danych.</span><span class="sxs-lookup"><span data-stu-id="be601-124">Call the static <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> method while passing an array of bytes to decrypt and the data protection scope.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be601-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="be601-125">Example</span></span>  
 <span data-ttu-id="be601-126">Poniższy przykład kodu ilustruje dwie formy szyfrowania i odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="be601-126">The following code example demonstrates two forms of encryption and decryption.</span></span>  <span data-ttu-id="be601-127">Najpierw kod szyfruje, a następnie odszyfrowuje tablicę bajtów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="be601-127">First, the code example encrypts and then decrypts an in-memory array of bytes.</span></span>  <span data-ttu-id="be601-128">W przykładzie kod szyfruje kopię tablicy bajtowej, zapisuje ją w pliku, ładuje dane z powrotem z pliku, a następnie odszyfrowuje dane.</span><span class="sxs-lookup"><span data-stu-id="be601-128">Next, the code example encrypts a copy of a byte array, saves it to a file, loads the data back from the file, and then decrypts the data.</span></span>  <span data-ttu-id="be601-129">Przykład wyświetla oryginalne dane, zaszyfrowane dane i odszyfrowane dane.</span><span class="sxs-lookup"><span data-stu-id="be601-129">The example displays the original data, the encrypted data, and the decrypted data.</span></span>  
  
 [!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
 [!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="be601-130">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="be601-130">Compiling the Code</span></span>  
  
- <span data-ttu-id="be601-131">Dołącz odwołanie do `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="be601-131">Include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="be601-132">Dołącz <xref:System> <xref:System.IO> <xref:System.Security.Cryptography> przestrzeń nazw,,, i <xref:System.Text> .</span><span class="sxs-lookup"><span data-stu-id="be601-132">Include the <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography>, and <xref:System.Text> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be601-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="be601-133">See also</span></span>

- <xref:System.Security.Cryptography.ProtectedMemory>
- <xref:System.Security.Cryptography.ProtectedData>
