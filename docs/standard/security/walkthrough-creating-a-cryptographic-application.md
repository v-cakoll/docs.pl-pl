---
title: "Wskazówki: tworzenie aplikacji kryptograficznej"
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
- cryptography [NET Framework], example
- cryptography [NET Framework], cryptographic application example
- cryptography [NET Framework], application example
ms.assetid: abf48c11-1e72-431d-9562-39cf23e1a8ff
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 869d35a15a028e6df09dea281ac653ab8b9a28d6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="walkthrough-creating-a-cryptographic-application"></a><span data-ttu-id="cda30-102">Wskazówki: tworzenie aplikacji kryptograficznej</span><span class="sxs-lookup"><span data-stu-id="cda30-102">Walkthrough: Creating a Cryptographic Application</span></span>
<span data-ttu-id="cda30-103">W tym przewodniku pokazano, jak do szyfrowania i odszyfrowywania zawartości.</span><span class="sxs-lookup"><span data-stu-id="cda30-103">This walkthrough demonstrates how to encrypt and decrypt content.</span></span> <span data-ttu-id="cda30-104">Przykłady kodu są przeznaczone dla aplikacji formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="cda30-104">The code examples are designed for a Windows Forms application.</span></span> <span data-ttu-id="cda30-105">Ta aplikacja nie wykazują rzeczywistych scenariuszach, takich jak za pomocą kart inteligentnych.</span><span class="sxs-lookup"><span data-stu-id="cda30-105">This application does not demonstrate real world scenarios, such as using smart cards.</span></span> <span data-ttu-id="cda30-106">Zamiast tego należy go przedstawiono podstawowe informacje dotyczące szyfrowania i odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="cda30-106">Instead, it demonstrates the fundamentals of encryption and decryption.</span></span>  
  
 <span data-ttu-id="cda30-107">W tym przewodniku zastosowano następujące wytyczne szyfrowania:</span><span class="sxs-lookup"><span data-stu-id="cda30-107">This walkthrough uses the following guidelines for encryption:</span></span>  
  
-   <span data-ttu-id="cda30-108">Użyj <xref:System.Security.Cryptography.RijndaelManaged> klasy algorytmu symetrycznego, do szyfrowania i odszyfrowywania danych przy użyciu jego automatycznie generowanych <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> i <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>.</span><span class="sxs-lookup"><span data-stu-id="cda30-108">Use the <xref:System.Security.Cryptography.RijndaelManaged> class, a symmetric algorithm, to encrypt and decrypt data by using its automatically generated <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> and <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>.</span></span>  
  
-   <span data-ttu-id="cda30-109">Użyj <xref:System.Security.Cryptography.RSACryptoServiceProvider>, algorytmu asymetrycznego, do szyfrowania i odszyfrowywania klucza do danych zaszyfrowanych przez <xref:System.Security.Cryptography.RijndaelManaged>.</span><span class="sxs-lookup"><span data-stu-id="cda30-109">Use the <xref:System.Security.Cryptography.RSACryptoServiceProvider>, an asymmetric algorithm, to encrypt and decrypt the key to the data encrypted by <xref:System.Security.Cryptography.RijndaelManaged>.</span></span> <span data-ttu-id="cda30-110">Asymetryczne algorytmy najlepiej są używane w przypadku mniejszych ilości danych, takich jak klucza.</span><span class="sxs-lookup"><span data-stu-id="cda30-110">Asymmetric algorithms are best used for smaller amounts of data, such as a key.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cda30-111">Aby chronić dane na komputerze zamiast wymiany zaszyfrowaną zawartość z innych osób, należy rozważyć użycie <xref:System.Security.Cryptography.ProtectedData> lub <xref:System.Security.Cryptography.ProtectedMemory> klasy.</span><span class="sxs-lookup"><span data-stu-id="cda30-111">If you want to protect data on your computer instead of exchanging encrypted content with other people, consider using the <xref:System.Security.Cryptography.ProtectedData> or <xref:System.Security.Cryptography.ProtectedMemory> classes.</span></span>  
  
 <span data-ttu-id="cda30-112">W poniższej tabeli przedstawiono zadania kryptograficzne, w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="cda30-112">The following table summarizes the cryptographic tasks in this topic.</span></span>  
  
|<span data-ttu-id="cda30-113">Zadanie</span><span class="sxs-lookup"><span data-stu-id="cda30-113">Task</span></span>|<span data-ttu-id="cda30-114">Opis</span><span class="sxs-lookup"><span data-stu-id="cda30-114">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="cda30-115">Tworzenie aplikacji formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="cda30-115">Creating a Windows Forms application</span></span>|<span data-ttu-id="cda30-116">Zawiera listę funkcji, które są wymagane do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cda30-116">Lists the controls that are required to run the application.</span></span>|  
|<span data-ttu-id="cda30-117">Deklarowanie obiektów globalnych</span><span class="sxs-lookup"><span data-stu-id="cda30-117">Declaring global objects</span></span>|<span data-ttu-id="cda30-118">Deklaruje zmienne ścieżek w ciągu <xref:System.Security.Cryptography.CspParameters>i <xref:System.Security.Cryptography.RSACryptoServiceProvider> ma globalne kontekście <xref:System.Windows.Forms.Form> klasy.</span><span class="sxs-lookup"><span data-stu-id="cda30-118">Declares string path variables, the <xref:System.Security.Cryptography.CspParameters>, and the <xref:System.Security.Cryptography.RSACryptoServiceProvider> to have global context of the <xref:System.Windows.Forms.Form> class.</span></span>|  
|<span data-ttu-id="cda30-119">Tworzenie klucza asymetrycznego</span><span class="sxs-lookup"><span data-stu-id="cda30-119">Creating an asymmetric key</span></span>|<span data-ttu-id="cda30-120">Tworzy asymetrycznego publiczne i prywatne para klucz-wartość i przypisuje mu nazwę kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="cda30-120">Creates an asymmetric public and private key value pair and assigns it a key container name.</span></span>|  
|<span data-ttu-id="cda30-121">System szyfrowania plików</span><span class="sxs-lookup"><span data-stu-id="cda30-121">Encrypting a file</span></span>|<span data-ttu-id="cda30-122">Wyświetla okno dialogowe, aby wybrać plik do szyfrowania i szyfruje plik.</span><span class="sxs-lookup"><span data-stu-id="cda30-122">Displays a dialog box to select a file for encryption and encrypts the file.</span></span>|  
|<span data-ttu-id="cda30-123">Odszyfrowywanie pliku</span><span class="sxs-lookup"><span data-stu-id="cda30-123">Decrypting a file</span></span>|<span data-ttu-id="cda30-124">Wyświetla okno dialogowe, aby wybrać zaszyfrowanego pliku do odszyfrowywania i odszyfrowuje pliku.</span><span class="sxs-lookup"><span data-stu-id="cda30-124">Displays a dialog box to select an encrypted file for decryption and decrypts the file.</span></span>|  
|<span data-ttu-id="cda30-125">Wprowadzenie klucza prywatnego.</span><span class="sxs-lookup"><span data-stu-id="cda30-125">Getting a private key</span></span>|<span data-ttu-id="cda30-126">Pobiera pary pełnej kluczy przy użyciu nazwy kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="cda30-126">Gets the full key pair using the key container name.</span></span>|  
|<span data-ttu-id="cda30-127">Eksportowanie klucza publicznego</span><span class="sxs-lookup"><span data-stu-id="cda30-127">Exporting a public key</span></span>|<span data-ttu-id="cda30-128">Klucz jest zapisywany do pliku XML z tylko publiczne parametrów.</span><span class="sxs-lookup"><span data-stu-id="cda30-128">Saves the key to an XML file with only public parameters.</span></span>|  
|<span data-ttu-id="cda30-129">Importowanie klucza publicznego</span><span class="sxs-lookup"><span data-stu-id="cda30-129">Importing a public key</span></span>|<span data-ttu-id="cda30-130">Ładuje klucz z pliku XML do kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="cda30-130">Loads the key from an XML file into the key container.</span></span>|  
|<span data-ttu-id="cda30-131">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="cda30-131">Testing the application</span></span>|<span data-ttu-id="cda30-132">Zawiera listę procedur do testowania tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cda30-132">Lists procedures for testing this application.</span></span>|  
  
## <a name="prerequisites"></a><span data-ttu-id="cda30-133">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="cda30-133">Prerequisites</span></span>  
 <span data-ttu-id="cda30-134">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="cda30-134">You need the following components to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="cda30-135">Odwołuje się do <xref:System.IO> i <xref:System.Security.Cryptography> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="cda30-135">References to the <xref:System.IO> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
## <a name="creating-a-windows-forms-application"></a><span data-ttu-id="cda30-136">Tworzenie aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cda30-136">Creating a Windows Forms Application</span></span>  
 <span data-ttu-id="cda30-137">Większość przykładów kodu, w tym przewodniku są zaprojektowane jako programy obsługi zdarzeń dla kontrolek przycisku.</span><span class="sxs-lookup"><span data-stu-id="cda30-137">Most of the code examples in this walkthrough are designed to be event handlers for button controls.</span></span> <span data-ttu-id="cda30-138">W poniższej tabeli wymieniono formantów, wymaganych do przykładowej aplikacji i ich nazw wymagane zgodne z przykładami kodu.</span><span class="sxs-lookup"><span data-stu-id="cda30-138">The following table lists the controls required for the sample application and their required names to match the code examples.</span></span>  
  
|<span data-ttu-id="cda30-139">Formant</span><span class="sxs-lookup"><span data-stu-id="cda30-139">Control</span></span>|<span data-ttu-id="cda30-140">Nazwa</span><span class="sxs-lookup"><span data-stu-id="cda30-140">Name</span></span>|<span data-ttu-id="cda30-141">Właściwość Text (w razie potrzeby)</span><span class="sxs-lookup"><span data-stu-id="cda30-141">Text property (as needed)</span></span>|  
|-------------|----------|---------------------------------|  
|<xref:System.Windows.Forms.Button>|`buttonEncryptFile`|<span data-ttu-id="cda30-142">Szyfrowanie plików</span><span class="sxs-lookup"><span data-stu-id="cda30-142">Encrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonDecryptFile`|<span data-ttu-id="cda30-143">Odszyfrowywania plików</span><span class="sxs-lookup"><span data-stu-id="cda30-143">Decrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonCreateAsmKeys`|<span data-ttu-id="cda30-144">Tworzenie kluczy</span><span class="sxs-lookup"><span data-stu-id="cda30-144">Create Keys</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonExportPublicKey`|<span data-ttu-id="cda30-145">Wyeksportować klucz publiczny</span><span class="sxs-lookup"><span data-stu-id="cda30-145">Export Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonImportPublicKey`|<span data-ttu-id="cda30-146">Importuj klucz publiczny</span><span class="sxs-lookup"><span data-stu-id="cda30-146">Import Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonGetPrivateKey`|<span data-ttu-id="cda30-147">Pobierz klucz prywatny</span><span class="sxs-lookup"><span data-stu-id="cda30-147">Get Private Key</span></span>|  
|<xref:System.Windows.Forms.Label>|`label1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog2`||  
  
 <span data-ttu-id="cda30-148">Kliknij dwukrotnie przycisków w projektancie programu Visual Studio do tworzenia swoich programów obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="cda30-148">Double-click the buttons in the  Visual Studio designer to create their event handlers.</span></span>  
  
## <a name="declaring-global-objects"></a><span data-ttu-id="cda30-149">Deklarowanie obiektów globalnych</span><span class="sxs-lookup"><span data-stu-id="cda30-149">Declaring Global Objects</span></span>  
 <span data-ttu-id="cda30-150">Dodaj następujący kod do konstruktora formularza.</span><span class="sxs-lookup"><span data-stu-id="cda30-150">Add the following code to the Form's constructor.</span></span> <span data-ttu-id="cda30-151">Edytowanie zmiennych ciągu dla Twojego środowiska i swoich preferencji.</span><span class="sxs-lookup"><span data-stu-id="cda30-151">Edit the string variables for your environment and preferences.</span></span>  
  
 [!code-csharp[CryptoWalkThru#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#1)]
 [!code-vb[CryptoWalkThru#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#1)]  
  
## <a name="creating-an-asymmetric-key"></a><span data-ttu-id="cda30-152">Tworzenie klucza asymetrycznego</span><span class="sxs-lookup"><span data-stu-id="cda30-152">Creating an Asymmetric Key</span></span>  
 <span data-ttu-id="cda30-153">To zadanie tworzy klucza asymetrycznego, który szyfruje i odszyfrowuje <xref:System.Security.Cryptography.RijndaelManaged> klucza.</span><span class="sxs-lookup"><span data-stu-id="cda30-153">This task creates an asymmetric key that encrypts and decrypts the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span> <span data-ttu-id="cda30-154">Ten klucz został użyty do zaszyfrowania zawartości i wyświetla nazwę kontenera klucza na formantu etykiety.</span><span class="sxs-lookup"><span data-stu-id="cda30-154">This key was used to encrypt the content and it displays the key container name on the label control.</span></span>  
  
 <span data-ttu-id="cda30-155">Dodaj następujący kod jako `Click` programu obsługi zdarzeń dla `Create Keys` przycisk (`buttonCreateAsmKeys_Click`).</span><span class="sxs-lookup"><span data-stu-id="cda30-155">Add the following code as the `Click` event handler for the `Create Keys` button (`buttonCreateAsmKeys_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#2)]
 [!code-vb[CryptoWalkThru#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#2)]  
  
## <a name="encrypting-a-file"></a><span data-ttu-id="cda30-156">System szyfrowania plików</span><span class="sxs-lookup"><span data-stu-id="cda30-156">Encrypting a File</span></span>  
 <span data-ttu-id="cda30-157">To zadanie obejmuje dwie metody: metoda obsługi zdarzeń dla `Encrypt File` przycisk (`buttonEncryptFile_Click`) i `EncryptFile` metody.</span><span class="sxs-lookup"><span data-stu-id="cda30-157">This task involves two methods: the event handler method for the `Encrypt File` button (`buttonEncryptFile_Click`) and the `EncryptFile` method.</span></span> <span data-ttu-id="cda30-158">Pierwsza metoda Wyświetla okno dialogowe wybierania pliku i przekazuje nazwę pliku do drugiej metody, która wykonuje szyfrowanie.</span><span class="sxs-lookup"><span data-stu-id="cda30-158">The first method displays a dialog box for selecting a file and passes the file name to the second method, which performs the encryption.</span></span>  
  
 <span data-ttu-id="cda30-159">Zaszyfrowaną zawartość, klucz i IV są zapisywane do jednego <xref:System.IO.FileStream>, który jest określany jako pakietu szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="cda30-159">The encrypted content, key, and IV are all saved to one <xref:System.IO.FileStream>, which is referred to as the encryption package.</span></span>  
  
 <span data-ttu-id="cda30-160">`EncryptFile` Metoda wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="cda30-160">The `EncryptFile` method does the following:</span></span>  
  
1.  <span data-ttu-id="cda30-161">Tworzy <xref:System.Security.Cryptography.RijndaelManaged> algorytmu symetrycznego zawartość.</span><span class="sxs-lookup"><span data-stu-id="cda30-161">Creates a <xref:System.Security.Cryptography.RijndaelManaged> symmetric algorithm to encrypt the content.</span></span>  
  
2.  <span data-ttu-id="cda30-162">Tworzy <xref:System.Security.Cryptography.RSACryptoServiceProvider> obiektu do szyfrowania <xref:System.Security.Cryptography.RijndaelManaged> klucza.</span><span class="sxs-lookup"><span data-stu-id="cda30-162">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to encrypt the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span>  
  
3.  <span data-ttu-id="cda30-163">Używa <xref:System.Security.Cryptography.CryptoStream> obiektu do odczytu i szyfrowania <xref:System.IO.FileStream> pliku źródłowego w blokach bajtów do miejsca docelowego <xref:System.IO.FileStream> obiektu dla zaszyfrowany plik.</span><span class="sxs-lookup"><span data-stu-id="cda30-163">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and encrypt the <xref:System.IO.FileStream> of the source file, in blocks of bytes, into a destination <xref:System.IO.FileStream> object for the encrypted file.</span></span>  
  
4.  <span data-ttu-id="cda30-164">Określa długość zaszyfrowanego klucza i IV i tworzy tablice typu byte ich wartości długości.</span><span class="sxs-lookup"><span data-stu-id="cda30-164">Determines the lengths of the encrypted key and IV, and creates byte arrays of their length values.</span></span>  
  
5.  <span data-ttu-id="cda30-165">Zapisuje klucz, IV i ich wartości długości zaszyfrowanego pakietu.</span><span class="sxs-lookup"><span data-stu-id="cda30-165">Writes the Key, IV, and their length values to the encrypted package.</span></span>  
  
 <span data-ttu-id="cda30-166">Pakietu szyfrowania używany następujący format:</span><span class="sxs-lookup"><span data-stu-id="cda30-166">The encryption package uses the following format:</span></span>  
  
-   <span data-ttu-id="cda30-167">Długość klucza bajtów 0 - 3</span><span class="sxs-lookup"><span data-stu-id="cda30-167">Key length, bytes 0 - 3</span></span>  
  
-   <span data-ttu-id="cda30-168">Długość IV, bajtów 4-7</span><span class="sxs-lookup"><span data-stu-id="cda30-168">IV length, bytes 4 - 7</span></span>  
  
-   <span data-ttu-id="cda30-169">Zaszyfrowany klucz</span><span class="sxs-lookup"><span data-stu-id="cda30-169">Encrypted key</span></span>  
  
-   <span data-ttu-id="cda30-170">IV</span><span class="sxs-lookup"><span data-stu-id="cda30-170">IV</span></span>  
  
-   <span data-ttu-id="cda30-171">Tekst zaszyfrowany</span><span class="sxs-lookup"><span data-stu-id="cda30-171">Cipher text</span></span>  
  
 <span data-ttu-id="cda30-172">Długość klucza i IV służy do określenia punkty początkowy i długości wszystkie części pakietu szyfrowania, które mogą być następnie używane do odszyfrowywania pliku.</span><span class="sxs-lookup"><span data-stu-id="cda30-172">You can use the lengths of the key and IV to determine the starting points and lengths of all parts of the encryption package, which can then be used to decrypt the file.</span></span>  
  
 <span data-ttu-id="cda30-173">Dodaj następujący kod jako `Click` programu obsługi zdarzeń dla `Encrypt File` przycisk (`buttonEncryptFile_Click`).</span><span class="sxs-lookup"><span data-stu-id="cda30-173">Add the following code as the `Click` event handler for the `Encrypt File` button (`buttonEncryptFile_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#3)]
 [!code-vb[CryptoWalkThru#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#3)]  
  
 <span data-ttu-id="cda30-174">Dodaj następujące `EncryptFile` metody do formularza.</span><span class="sxs-lookup"><span data-stu-id="cda30-174">Add the following `EncryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#5)]
 [!code-vb[CryptoWalkThru#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#5)]  
  
## <a name="decrypting-a-file"></a><span data-ttu-id="cda30-175">Odszyfrowywanie pliku</span><span class="sxs-lookup"><span data-stu-id="cda30-175">Decrypting a File</span></span>  
 <span data-ttu-id="cda30-176">To zadanie obejmuje dwie metody, metoda obsługi zdarzeń dla `Decrypt File` przycisk (`buttonEncryptFile_Click`) i `DecryptFile` metody.</span><span class="sxs-lookup"><span data-stu-id="cda30-176">This task involves two methods, the event handler method for the `Decrypt File` button (`buttonEncryptFile_Click`), and the `DecryptFile` method.</span></span> <span data-ttu-id="cda30-177">Pierwsza metoda Wyświetla okno dialogowe wybierania pliku i przekazuje jego nazwa pliku do drugiej metody, która wykonuje odszyfrowywanie.</span><span class="sxs-lookup"><span data-stu-id="cda30-177">The first method displays a dialog box for selecting a file and passes its file name to the second method, which performs the decryption.</span></span>  
  
 <span data-ttu-id="cda30-178">`Decrypt` Metoda wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="cda30-178">The `Decrypt` method does the following:</span></span>  
  
1.  <span data-ttu-id="cda30-179">Tworzy <xref:System.Security.Cryptography.RijndaelManaged> algorytmu symetrycznego do odszyfrowywania zawartości.</span><span class="sxs-lookup"><span data-stu-id="cda30-179">Creates a <xref:System.Security.Cryptography.RijndaelManaged> symmetric algorithm to decrypt the content.</span></span>  
  
2.  <span data-ttu-id="cda30-180">Odczytuje pierwszych osiem bajtów <xref:System.IO.FileStream> zaszyfrowanego pakietu do tablic bajtowych można uzyskać długości zaszyfrowanego klucza i IV.</span><span class="sxs-lookup"><span data-stu-id="cda30-180">Reads the first eight bytes of the <xref:System.IO.FileStream> of the encrypted package into byte arrays to obtain the lengths of the encrypted key and the IV.</span></span>  
  
3.  <span data-ttu-id="cda30-181">Pobiera klucz i IV z pakietu szyfrowania na tablice typu byte.</span><span class="sxs-lookup"><span data-stu-id="cda30-181">Extracts the key and IV from the encryption package into byte arrays.</span></span>  
  
4.  <span data-ttu-id="cda30-182">Tworzy <xref:System.Security.Cryptography.RSACryptoServiceProvider> obiektu do odszyfrowania <xref:System.Security.Cryptography.RijndaelManaged> klucza.</span><span class="sxs-lookup"><span data-stu-id="cda30-182">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to decrypt the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span>  
  
5.  <span data-ttu-id="cda30-183">Używa <xref:System.Security.Cryptography.CryptoStream> obiektu do odczytu i do odszyfrowywania sekcji tekstu szyfrowania <xref:System.IO.FileStream> szyfrowania pakietów, w blokach bajtów w <xref:System.IO.FileStream> obiektu odszyfrowane pliku.</span><span class="sxs-lookup"><span data-stu-id="cda30-183">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and decrypt the cipher text section of the <xref:System.IO.FileStream> encryption package, in blocks of bytes, into the <xref:System.IO.FileStream> object for the decrypted file.</span></span> <span data-ttu-id="cda30-184">Po jej zakończeniu, odszyfrowywanie zostało ukończone.</span><span class="sxs-lookup"><span data-stu-id="cda30-184">When this is finished, the decryption is completed.</span></span>  
  
 <span data-ttu-id="cda30-185">Dodaj następujący kod jako `Click` programu obsługi zdarzeń dla `Decrypt File` przycisku.</span><span class="sxs-lookup"><span data-stu-id="cda30-185">Add the following code as the `Click` event handler for the `Decrypt File` button.</span></span>  
  
 [!code-csharp[CryptoWalkThru#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#4)]
 [!code-vb[CryptoWalkThru#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#4)]  
  
 <span data-ttu-id="cda30-186">Dodaj następujące `DecryptFile` metody do formularza.</span><span class="sxs-lookup"><span data-stu-id="cda30-186">Add the following `DecryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#6)]
 [!code-vb[CryptoWalkThru#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#6)]  
  
## <a name="exporting-a-public-key"></a><span data-ttu-id="cda30-187">Eksportowanie klucza publicznego</span><span class="sxs-lookup"><span data-stu-id="cda30-187">Exporting a Public Key</span></span>  
 <span data-ttu-id="cda30-188">To zadanie jest zapisywany klucza utworzonego na podstawie `Create Keys` przycisku do pliku.</span><span class="sxs-lookup"><span data-stu-id="cda30-188">This task saves the key created by the `Create Keys` button to a file.</span></span> <span data-ttu-id="cda30-189">Eksportuje go tylko publiczne parametrów.</span><span class="sxs-lookup"><span data-stu-id="cda30-189">It exports only the public parameters.</span></span>  
  
 <span data-ttu-id="cda30-190">To zadanie symuluje scenariusza Alicja nadanie Bob jej klucz publiczny, aby on szyfrowania plików dla jej.</span><span class="sxs-lookup"><span data-stu-id="cda30-190">This task simulates the scenario of Alice giving Bob her public key so that he can encrypt files for her.</span></span> <span data-ttu-id="cda30-191">On i innych użytkowników mających tego klucza publicznego nie będą stanie ich odszyfrować, ponieważ nie mają pary pełnej kluczy prywatnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="cda30-191">He and others who have that public key will not be able to decrypt them because they do not have the full key pair with private parameters.</span></span>  
  
 <span data-ttu-id="cda30-192">Dodaj następujący kod jako `Click` programu obsługi zdarzeń dla `Export Public Key` przycisk (`buttonExportPublicKey_Click`).</span><span class="sxs-lookup"><span data-stu-id="cda30-192">Add the following code as the `Click` event handler for the `Export Public Key` button (`buttonExportPublicKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#8)]
 [!code-vb[CryptoWalkThru#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#8)]  
  
## <a name="importing-a-public-key"></a><span data-ttu-id="cda30-193">Importowanie klucza publicznego</span><span class="sxs-lookup"><span data-stu-id="cda30-193">Importing a Public Key</span></span>  
 <span data-ttu-id="cda30-194">To zadanie ładuje klucza z parametrami tylko publiczne, tworzony przez `Export Public Key` przycisk i ustawia go jako nazwa kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="cda30-194">This task loads the key with only public parameters, as created by the `Export Public Key` button, and sets it as the key container name.</span></span>  
  
 <span data-ttu-id="cda30-195">To zadanie symuluje scenariusza Bob ładowania klucza Alicji parametrami tylko publiczne, więc on szyfrowania plików dla jej.</span><span class="sxs-lookup"><span data-stu-id="cda30-195">This task simulates the scenario of Bob loading Alice's key with only public parameters so he can encrypt files for her.</span></span>  
  
 <span data-ttu-id="cda30-196">Dodaj następujący kod jako `Click` programu obsługi zdarzeń dla `Import Public Key` przycisk (`buttonImportPublicKey_Click`).</span><span class="sxs-lookup"><span data-stu-id="cda30-196">Add the following code as the `Click` event handler for the `Import Public Key` button (`buttonImportPublicKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#9)]
 [!code-vb[CryptoWalkThru#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#9)]  
  
## <a name="getting-a-private-key"></a><span data-ttu-id="cda30-197">Wprowadzenie klucza prywatnego</span><span class="sxs-lookup"><span data-stu-id="cda30-197">Getting a Private Key</span></span>  
 <span data-ttu-id="cda30-198">To zadanie umożliwia ustawienie nazwy kontenera kluczy nazwę klucza utworzone za pomocą `Create Keys` przycisku.</span><span class="sxs-lookup"><span data-stu-id="cda30-198">This task sets the key container name to the name of the key created by using the `Create Keys` button.</span></span> <span data-ttu-id="cda30-199">Kontener kluczy będzie zawierać pary pełnej kluczy prywatnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="cda30-199">The key container will contain the full key pair with private parameters.</span></span>  
  
 <span data-ttu-id="cda30-200">To zadanie symuluje scenariusza Alicji przy użyciu swojego klucza prywatnego do odszyfrowywania plików zaszyfrowanych przez niego.</span><span class="sxs-lookup"><span data-stu-id="cda30-200">This task simulates the scenario of Alice using her private key to decrypt files encrypted by Bob.</span></span>  
  
 <span data-ttu-id="cda30-201">Dodaj następujący kod jako `Click` programu obsługi zdarzeń dla `Get Private Key` przycisk (`buttonGetPrivateKey_Click`).</span><span class="sxs-lookup"><span data-stu-id="cda30-201">Add the following code as the `Click` event handler for the `Get Private Key` button (`buttonGetPrivateKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#7)]
 [!code-vb[CryptoWalkThru#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#7)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="cda30-202">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="cda30-202">Testing the Application</span></span>  
 <span data-ttu-id="cda30-203">Po skonstruowaniu aplikacji, należy wykonać następujące scenariusze testowania.</span><span class="sxs-lookup"><span data-stu-id="cda30-203">After you have built the application, perform the following testing scenarios.</span></span>  
  
#### <a name="to-create-keys-encrypt-and-decrypt"></a><span data-ttu-id="cda30-204">Do tworzenia kluczy, szyfrowania i odszyfrowywania</span><span class="sxs-lookup"><span data-stu-id="cda30-204">To create keys, encrypt, and decrypt</span></span>  
  
1.  <span data-ttu-id="cda30-205">Kliknij przycisk `Create Keys` przycisku.</span><span class="sxs-lookup"><span data-stu-id="cda30-205">Click the `Create Keys` button.</span></span> <span data-ttu-id="cda30-206">Etykieta Wyświetla nazwę klucza i wskazuje, że jest pary kluczy pełnej.</span><span class="sxs-lookup"><span data-stu-id="cda30-206">The label displays the key name and shows that it is a full key pair.</span></span>  
  
2.  <span data-ttu-id="cda30-207">Kliknij przycisk `Export Public Key` przycisku.</span><span class="sxs-lookup"><span data-stu-id="cda30-207">Click the `Export Public Key` button.</span></span> <span data-ttu-id="cda30-208">Należy pamiętać, że eksportowanie parametrów klucza publicznego nie zmienia się bieżący klucz.</span><span class="sxs-lookup"><span data-stu-id="cda30-208">Note that exporting the public key parameters does not change the current key.</span></span>  
  
3.  <span data-ttu-id="cda30-209">Kliknij przycisk `Encrypt File` i wybrać plik.</span><span class="sxs-lookup"><span data-stu-id="cda30-209">Click the `Encrypt File` button and select a file.</span></span>  
  
4.  <span data-ttu-id="cda30-210">Kliknij przycisk `Decrypt File` i wybrać plik tylko zaszyfrowane.</span><span class="sxs-lookup"><span data-stu-id="cda30-210">Click the `Decrypt File` button and select the file just encrypted.</span></span>  
  
5.  <span data-ttu-id="cda30-211">Zapoznaj się z plikiem tylko odszyfrować.</span><span class="sxs-lookup"><span data-stu-id="cda30-211">Examine the file just decrypted.</span></span>  
  
6.  <span data-ttu-id="cda30-212">Zamknij aplikację i uruchom ponownie, aby przetestować pobieranie utrwalonych kontenerów kluczy w scenariuszu dalej.</span><span class="sxs-lookup"><span data-stu-id="cda30-212">Close the application and restart it to test retrieving persisted key containers in the next scenario.</span></span>  
  
#### <a name="to-encrypt-using-the-public-key"></a><span data-ttu-id="cda30-213">Do szyfrowania za pomocą klucza publicznego</span><span class="sxs-lookup"><span data-stu-id="cda30-213">To encrypt using the public key</span></span>  
  
1.  <span data-ttu-id="cda30-214">Kliknij przycisk `Import Public Key` przycisku.</span><span class="sxs-lookup"><span data-stu-id="cda30-214">Click the `Import Public Key` button.</span></span> <span data-ttu-id="cda30-215">Etykieta Wyświetla nazwę klucza i wskazuje, że jest publiczny wyłącznie.</span><span class="sxs-lookup"><span data-stu-id="cda30-215">The label displays the key name and shows that it is public only.</span></span>  
  
2.  <span data-ttu-id="cda30-216">Kliknij przycisk `Encrypt File` i wybrać plik.</span><span class="sxs-lookup"><span data-stu-id="cda30-216">Click the `Encrypt File` button and select a file.</span></span>  
  
3.  <span data-ttu-id="cda30-217">Kliknij przycisk `Decrypt File` i wybrać plik tylko zaszyfrowane.</span><span class="sxs-lookup"><span data-stu-id="cda30-217">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="cda30-218">To zakończy się niepowodzeniem, ponieważ musi mieć klucz prywatny do odszyfrowania.</span><span class="sxs-lookup"><span data-stu-id="cda30-218">This will fail because you must have the private key to decrypt.</span></span>  
  
 <span data-ttu-id="cda30-219">W tym scenariuszu pokazano, po klucz publiczny do zaszyfrowania pliku innej osoby.</span><span class="sxs-lookup"><span data-stu-id="cda30-219">This scenario demonstrates having only the public key to encrypt a file for another person.</span></span> <span data-ttu-id="cda30-220">Zwykle ta osoba umożliwiają tylko klucz publiczny i wstrzymania klucza prywatnego do odszyfrowania.</span><span class="sxs-lookup"><span data-stu-id="cda30-220">Typically that person would give you only the public key and withhold the private key for decryption.</span></span>  
  
#### <a name="to-decrypt-using-the-private-key"></a><span data-ttu-id="cda30-221">Można odszyfrować za pomocą klucza prywatnego</span><span class="sxs-lookup"><span data-stu-id="cda30-221">To decrypt using the private key</span></span>  
  
1.  <span data-ttu-id="cda30-222">Kliknij przycisk `Get Private Key` przycisku.</span><span class="sxs-lookup"><span data-stu-id="cda30-222">Click the `Get Private Key` button.</span></span> <span data-ttu-id="cda30-223">Etykieta Wyświetla nazwę klucza i wskazuje, czy jest pary kluczy pełnej.</span><span class="sxs-lookup"><span data-stu-id="cda30-223">The label displays the key name and shows whether it is the full key pair.</span></span>  
  
2.  <span data-ttu-id="cda30-224">Kliknij przycisk `Decrypt File` i wybrać plik tylko zaszyfrowane.</span><span class="sxs-lookup"><span data-stu-id="cda30-224">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="cda30-225">Są to powiodło się ponieważ pary kluczy pełnej do odszyfrowania.</span><span class="sxs-lookup"><span data-stu-id="cda30-225">This will be successful because you have the full key pair to decrypt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cda30-226">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cda30-226">See Also</span></span>  
 [<span data-ttu-id="cda30-227">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="cda30-227">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
