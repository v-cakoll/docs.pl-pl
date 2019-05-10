---
title: 'Instrukcje: Stosowanie ochrony danych'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1dc8c75d3c8c91d974388779528deff16453d852
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64602536"
---
# <a name="how-to-use-data-protection"></a><span data-ttu-id="5cedf-102">Instrukcje: Stosowanie ochrony danych</span><span class="sxs-lookup"><span data-stu-id="5cedf-102">How to: Use Data Protection</span></span>
<span data-ttu-id="5cedf-103">.NET Framework zapewnia dostęp do ochrony danych interfejsu API (DPAPI), co pozwala na szyfrowanie danych, korzystając z informacji z bieżącego konta użytkownika lub komputera.</span><span class="sxs-lookup"><span data-stu-id="5cedf-103">The .NET Framework provides access to the data protection API (DPAPI), which allows you to encrypt data using information from the current user account or computer.</span></span>  <span data-ttu-id="5cedf-104">Korzystając z interfejsu DPAPI złagodzić się trudne problem jawnie generowania i przechowywania klucza kryptograficznego.</span><span class="sxs-lookup"><span data-stu-id="5cedf-104">When you use the DPAPI, you alleviate the difficult problem of explicitly generating and storing a cryptographic key.</span></span>  
  
 <span data-ttu-id="5cedf-105">Użyj <xref:System.Security.Cryptography.ProtectedMemory> klasy w celu zaszyfrowania tablicę bajtów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="5cedf-105">Use the <xref:System.Security.Cryptography.ProtectedMemory> class to encrypt an array of in-memory bytes.</span></span>  <span data-ttu-id="5cedf-106">Ta funkcja jest dostępna w systemie Microsoft Windows XP i nowszych systemach operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="5cedf-106">This functionality is available in Microsoft Windows XP and later operating systems.</span></span>  <span data-ttu-id="5cedf-107">Można określić pamięci zaszyfrowane przez bieżący proces odszyfrować je mogą tylko przez wszystkie procesy lub z tym samym kontekście użytkownika bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="5cedf-107">You can specify that memory encrypted by the current process can be decrypted by the current process only, by all processes, or from the same user context.</span></span>  <span data-ttu-id="5cedf-108">Zobacz <xref:System.Security.Cryptography.MemoryProtectionScope> wyliczenie, aby uzyskać szczegółowy opis <xref:System.Security.Cryptography.ProtectedMemory> opcje.</span><span class="sxs-lookup"><span data-stu-id="5cedf-108">See the <xref:System.Security.Cryptography.MemoryProtectionScope> enumeration for a detailed description of <xref:System.Security.Cryptography.ProtectedMemory> options.</span></span>  
  
 <span data-ttu-id="5cedf-109">Użyj <xref:System.Security.Cryptography.ProtectedData> klasy w celu zaszyfrowania kopiowania tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="5cedf-109">Use the <xref:System.Security.Cryptography.ProtectedData> class to encrypt a copy of an array of bytes.</span></span> <span data-ttu-id="5cedf-110">Ta funkcja jest dostępna w systemie Microsoft Windows 2000 i nowszych systemach operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="5cedf-110">This functionality is available in Microsoft Windows 2000 and later operating systems.</span></span>  <span data-ttu-id="5cedf-111">Można określić, czy dane są szyfrowane przy użyciu bieżącego konta użytkownika odszyfrować je mogą tylko tego samego konta użytkownika, lub można określić, że dane są szyfrowane przy użyciu bieżącego konta użytkownika można odszyfrować przez dowolne konto na komputerze.</span><span class="sxs-lookup"><span data-stu-id="5cedf-111">You can specify that data encrypted by the current user account can be decrypted only by the same user account, or you can specify that data encrypted by the current user account can be decrypted by any account on the computer.</span></span>  <span data-ttu-id="5cedf-112">Zobacz <xref:System.Security.Cryptography.DataProtectionScope> wyliczenie, aby uzyskać szczegółowy opis <xref:System.Security.Cryptography.ProtectedData> opcje.</span><span class="sxs-lookup"><span data-stu-id="5cedf-112">See the <xref:System.Security.Cryptography.DataProtectionScope> enumeration for a detailed description of <xref:System.Security.Cryptography.ProtectedData> options.</span></span>  
  
### <a name="to-encrypt-in-memory-data-using-data-protection"></a><span data-ttu-id="5cedf-113">Aby szyfrować dane w pamięci przy użyciu ochrony danych</span><span class="sxs-lookup"><span data-stu-id="5cedf-113">To encrypt in-memory data using data protection</span></span>  
  
1. <span data-ttu-id="5cedf-114">Wywołaj statyczną <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> metody podczas przekazując tablicę bajtów do szyfrowania, entropii i zakresu ochrony pamięci.</span><span class="sxs-lookup"><span data-stu-id="5cedf-114">Call the static <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> method while passing an array of bytes to encrypt, the entropy, and the memory protection scope.</span></span>  
  
### <a name="to-decrypt-in-memory-data-using-data-protection"></a><span data-ttu-id="5cedf-115">Aby odszyfrować dane w pamięci przy użyciu ochrony danych</span><span class="sxs-lookup"><span data-stu-id="5cedf-115">To decrypt in-memory data using data protection</span></span>  
  
1. <span data-ttu-id="5cedf-116">Wywołaj statyczną <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> metody podczas przekazywania tablica bajtów do odszyfrowania i zakresu ochrony pamięci.</span><span class="sxs-lookup"><span data-stu-id="5cedf-116">Call the static <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> method while passing an array of bytes to decrypt and the memory protection scope.</span></span>  
  
### <a name="to-encrypt-data-to-a-file-or-stream-using-data-protection"></a><span data-ttu-id="5cedf-117">Do szyfrowania danych do pliku lub strumienia za pomocą ochrony danych</span><span class="sxs-lookup"><span data-stu-id="5cedf-117">To encrypt data to a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="5cedf-118">Utwórz losowe entropii.</span><span class="sxs-lookup"><span data-stu-id="5cedf-118">Create random entropy.</span></span>  
  
2. <span data-ttu-id="5cedf-119">Wywołaj statyczną <xref:System.Security.Cryptography.ProtectedData.Protect%2A> metody podczas przekazując tablicę bajtów do szyfrowania, entropii i zakresu ochrony danych.</span><span class="sxs-lookup"><span data-stu-id="5cedf-119">Call the static <xref:System.Security.Cryptography.ProtectedData.Protect%2A> method while passing an array of bytes to encrypt, the entropy, and the data protection scope.</span></span>  
  
3. <span data-ttu-id="5cedf-120">Zaszyfrowane dane należy zapisać do pliku lub strumienia.</span><span class="sxs-lookup"><span data-stu-id="5cedf-120">Write the encrypted data to a file or stream.</span></span>  
  
### <a name="to-decrypt-data-from-a-file-or-stream-using-data-protection"></a><span data-ttu-id="5cedf-121">Aby odszyfrować dane z pliku lub strumienia za pomocą ochrony danych</span><span class="sxs-lookup"><span data-stu-id="5cedf-121">To decrypt data from a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="5cedf-122">Przeczytaj zaszyfrowane dane z pliku lub strumienia.</span><span class="sxs-lookup"><span data-stu-id="5cedf-122">Read the encrypted data from a file or stream.</span></span>  
  
2. <span data-ttu-id="5cedf-123">Wywołaj statyczną <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> metody podczas przekazywania tablica bajtów do odszyfrowania i zakresu ochrony danych.</span><span class="sxs-lookup"><span data-stu-id="5cedf-123">Call the static <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> method while passing an array of bytes to decrypt and the data protection scope.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cedf-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="5cedf-124">Example</span></span>  
 <span data-ttu-id="5cedf-125">Poniższy przykład kodu pokazuje dwa rodzaje szyfrowania i odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="5cedf-125">The following code example demonstrates two forms of encryption and decryption.</span></span>  <span data-ttu-id="5cedf-126">Po pierwsze w przykładzie kodu szyfruje i odszyfrowuje w pamięci tablica bajtów.</span><span class="sxs-lookup"><span data-stu-id="5cedf-126">First, the code example encrypts and then decrypts an in-memory array of bytes.</span></span>  <span data-ttu-id="5cedf-127">Następnie w przykładzie kodu szyfruje kopiowania tablicy bajtów, zapisuje w pliku, służy do ładowania danych z kopii pliku, a następnie odszyfrowuje dane.</span><span class="sxs-lookup"><span data-stu-id="5cedf-127">Next, the code example encrypts a copy of a byte array, saves it to a file, loads the data back from the file, and then decrypts the data.</span></span>  <span data-ttu-id="5cedf-128">W przykładzie wyświetlono oryginalne dane, zaszyfrowane dane i odszyfrowane dane.</span><span class="sxs-lookup"><span data-stu-id="5cedf-128">The example displays the original data, the encrypted data, and the decrypted data.</span></span>  
  
 [!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
 [!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5cedf-129">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="5cedf-129">Compiling the Code</span></span>  
  
- <span data-ttu-id="5cedf-130">Odwołanie do `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="5cedf-130">Include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="5cedf-131">Obejmują <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography>, i <xref:System.Text> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5cedf-131">Include the <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography>, and <xref:System.Text> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cedf-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5cedf-132">See also</span></span>

- <xref:System.Security.Cryptography.ProtectedMemory>
- <xref:System.Security.Cryptography.ProtectedData>
