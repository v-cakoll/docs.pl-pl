---
title: 'Porady: stosowanie ochrony danych'
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
ms.openlocfilehash: 0efd677f11189b28b8efc184c04b30a047ab942b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706035"
---
# <a name="how-to-use-data-protection"></a><span data-ttu-id="978d1-102">Porady: stosowanie ochrony danych</span><span class="sxs-lookup"><span data-stu-id="978d1-102">How to: Use Data Protection</span></span>
<span data-ttu-id="978d1-103">.NET Framework zapewnia dostęp do interfejsu API ochrony danych (DPAPI), który umożliwia szyfrowanie danych przy użyciu informacji z bieżącego konta użytkownika lub komputera.</span><span class="sxs-lookup"><span data-stu-id="978d1-103">The .NET Framework provides access to the data protection API (DPAPI), which allows you to encrypt data using information from the current user account or computer.</span></span>  <span data-ttu-id="978d1-104">Korzystając z interfejsu DPAPI, można złagodzić trudne problemy związane z jawnym generowaniem i przechowywaniem klucza kryptograficznego.</span><span class="sxs-lookup"><span data-stu-id="978d1-104">When you use the DPAPI, you alleviate the difficult problem of explicitly generating and storing a cryptographic key.</span></span>  
  
 <span data-ttu-id="978d1-105">Użyj klasy <xref:System.Security.Cryptography.ProtectedMemory>, aby zaszyfrować tablicę bajtów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="978d1-105">Use the <xref:System.Security.Cryptography.ProtectedMemory> class to encrypt an array of in-memory bytes.</span></span>  <span data-ttu-id="978d1-106">Ta funkcja jest dostępna w systemie Microsoft Windows XP i nowszych systemach operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="978d1-106">This functionality is available in Microsoft Windows XP and later operating systems.</span></span>  <span data-ttu-id="978d1-107">Można określić, że pamięć zaszyfrowana przez bieżący proces może zostać odszyfrowana tylko przez bieżący proces, przez wszystkie procesy lub z tego samego kontekstu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="978d1-107">You can specify that memory encrypted by the current process can be decrypted by the current process only, by all processes, or from the same user context.</span></span>  <span data-ttu-id="978d1-108">Aby uzyskać szczegółowy opis opcji <xref:System.Security.Cryptography.ProtectedMemory>, zobacz Wyliczenie <xref:System.Security.Cryptography.MemoryProtectionScope>.</span><span class="sxs-lookup"><span data-stu-id="978d1-108">See the <xref:System.Security.Cryptography.MemoryProtectionScope> enumeration for a detailed description of <xref:System.Security.Cryptography.ProtectedMemory> options.</span></span>  
  
 <span data-ttu-id="978d1-109">Użyj klasy <xref:System.Security.Cryptography.ProtectedData>, aby zaszyfrować kopię tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="978d1-109">Use the <xref:System.Security.Cryptography.ProtectedData> class to encrypt a copy of an array of bytes.</span></span> <span data-ttu-id="978d1-110">Ta funkcja jest dostępna w systemie Microsoft Windows 2000 i nowszych systemach operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="978d1-110">This functionality is available in Microsoft Windows 2000 and later operating systems.</span></span>  <span data-ttu-id="978d1-111">Możesz określić, że dane zaszyfrowane przez bieżące konto użytkownika mogą zostać odszyfrowane tylko przez to samo konto użytkownika, lub możesz określić, że dane zaszyfrowane przez bieżące konto użytkownika mogą zostać odszyfrowane za pomocą dowolnego konta na komputerze.</span><span class="sxs-lookup"><span data-stu-id="978d1-111">You can specify that data encrypted by the current user account can be decrypted only by the same user account, or you can specify that data encrypted by the current user account can be decrypted by any account on the computer.</span></span>  <span data-ttu-id="978d1-112">Aby uzyskać szczegółowy opis opcji <xref:System.Security.Cryptography.ProtectedData>, zobacz Wyliczenie <xref:System.Security.Cryptography.DataProtectionScope>.</span><span class="sxs-lookup"><span data-stu-id="978d1-112">See the <xref:System.Security.Cryptography.DataProtectionScope> enumeration for a detailed description of <xref:System.Security.Cryptography.ProtectedData> options.</span></span>  
  
### <a name="to-encrypt-in-memory-data-using-data-protection"></a><span data-ttu-id="978d1-113">Aby zaszyfrować dane znajdujące się w pamięci przy użyciu ochrony danych</span><span class="sxs-lookup"><span data-stu-id="978d1-113">To encrypt in-memory data using data protection</span></span>  
  
1. <span data-ttu-id="978d1-114">Wywołaj metodę static <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> podczas przekazywania tablicy bajtów do zaszyfrowania, entropii i zakresu ochrony pamięci.</span><span class="sxs-lookup"><span data-stu-id="978d1-114">Call the static <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> method while passing an array of bytes to encrypt, the entropy, and the memory protection scope.</span></span>  
  
### <a name="to-decrypt-in-memory-data-using-data-protection"></a><span data-ttu-id="978d1-115">Aby odszyfrować dane w pamięci przy użyciu ochrony danych</span><span class="sxs-lookup"><span data-stu-id="978d1-115">To decrypt in-memory data using data protection</span></span>  
  
1. <span data-ttu-id="978d1-116">Wywołaj metodę static <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> podczas przekazywania tablicy bajtów do odszyfrowania i zakresu ochrony pamięci.</span><span class="sxs-lookup"><span data-stu-id="978d1-116">Call the static <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> method while passing an array of bytes to decrypt and the memory protection scope.</span></span>  
  
### <a name="to-encrypt-data-to-a-file-or-stream-using-data-protection"></a><span data-ttu-id="978d1-117">Aby zaszyfrować dane do pliku lub strumienia przy użyciu ochrony danych</span><span class="sxs-lookup"><span data-stu-id="978d1-117">To encrypt data to a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="978d1-118">Utwórz entropię losową.</span><span class="sxs-lookup"><span data-stu-id="978d1-118">Create random entropy.</span></span>  
  
2. <span data-ttu-id="978d1-119">Wywołaj metodę static <xref:System.Security.Cryptography.ProtectedData.Protect%2A> podczas przekazywania tablicy bajtów do zaszyfrowania, entropii i zakresu ochrony danych.</span><span class="sxs-lookup"><span data-stu-id="978d1-119">Call the static <xref:System.Security.Cryptography.ProtectedData.Protect%2A> method while passing an array of bytes to encrypt, the entropy, and the data protection scope.</span></span>  
  
3. <span data-ttu-id="978d1-120">Zapisz dane zaszyfrowane do pliku lub strumienia.</span><span class="sxs-lookup"><span data-stu-id="978d1-120">Write the encrypted data to a file or stream.</span></span>  
  
### <a name="to-decrypt-data-from-a-file-or-stream-using-data-protection"></a><span data-ttu-id="978d1-121">Aby odszyfrować dane z pliku lub strumienia przy użyciu ochrony danych</span><span class="sxs-lookup"><span data-stu-id="978d1-121">To decrypt data from a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="978d1-122">Odczytaj zaszyfrowane dane z pliku lub strumienia.</span><span class="sxs-lookup"><span data-stu-id="978d1-122">Read the encrypted data from a file or stream.</span></span>  
  
2. <span data-ttu-id="978d1-123">Wywołaj metodę static <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> podczas przekazywania tablicy bajtów do odszyfrowania i zakresu ochrony danych.</span><span class="sxs-lookup"><span data-stu-id="978d1-123">Call the static <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> method while passing an array of bytes to decrypt and the data protection scope.</span></span>  
  
## <a name="example"></a><span data-ttu-id="978d1-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="978d1-124">Example</span></span>  
 <span data-ttu-id="978d1-125">Poniższy przykład kodu ilustruje dwie formy szyfrowania i odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="978d1-125">The following code example demonstrates two forms of encryption and decryption.</span></span>  <span data-ttu-id="978d1-126">Najpierw kod szyfruje, a następnie odszyfrowuje tablicę bajtów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="978d1-126">First, the code example encrypts and then decrypts an in-memory array of bytes.</span></span>  <span data-ttu-id="978d1-127">W przykładzie kod szyfruje kopię tablicy bajtowej, zapisuje ją w pliku, ładuje dane z powrotem z pliku, a następnie odszyfrowuje dane.</span><span class="sxs-lookup"><span data-stu-id="978d1-127">Next, the code example encrypts a copy of a byte array, saves it to a file, loads the data back from the file, and then decrypts the data.</span></span>  <span data-ttu-id="978d1-128">Przykład wyświetla oryginalne dane, zaszyfrowane dane i odszyfrowane dane.</span><span class="sxs-lookup"><span data-stu-id="978d1-128">The example displays the original data, the encrypted data, and the decrypted data.</span></span>  
  
 [!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
 [!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="978d1-129">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="978d1-129">Compiling the Code</span></span>  
  
- <span data-ttu-id="978d1-130">Dołącz odwołanie do `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="978d1-130">Include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="978d1-131">Uwzględnij przestrzeń nazw <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography>i <xref:System.Text>.</span><span class="sxs-lookup"><span data-stu-id="978d1-131">Include the <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography>, and <xref:System.Text> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="978d1-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="978d1-132">See also</span></span>

- <xref:System.Security.Cryptography.ProtectedMemory>
- <xref:System.Security.Cryptography.ProtectedData>
