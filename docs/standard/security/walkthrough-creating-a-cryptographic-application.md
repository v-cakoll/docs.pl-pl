---
title: 'Przewodnik: Tworzenie aplikacji kryptograficznej'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [NET Framework], example
- cryptography [NET Framework], cryptographic application example
- cryptography [NET Framework], application example
ms.assetid: abf48c11-1e72-431d-9562-39cf23e1a8ff
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5cdd2f5538be0e39b5dd3a378825ccf81f314c03
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916280"
---
# <a name="walkthrough-creating-a-cryptographic-application"></a><span data-ttu-id="9b655-102">Przewodnik: Tworzenie aplikacji kryptograficznej</span><span class="sxs-lookup"><span data-stu-id="9b655-102">Walkthrough: Creating a Cryptographic Application</span></span>
<span data-ttu-id="9b655-103">W tym instruktażu pokazano, jak szyfrować i odszyfrowywać zawartość.</span><span class="sxs-lookup"><span data-stu-id="9b655-103">This walkthrough demonstrates how to encrypt and decrypt content.</span></span> <span data-ttu-id="9b655-104">Przykłady kodu są przeznaczone dla aplikacji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="9b655-104">The code examples are designed for a Windows Forms application.</span></span> <span data-ttu-id="9b655-105">Ta aplikacja nie pokazuje rzeczywistych scenariuszy, takich jak korzystanie z kart inteligentnych.</span><span class="sxs-lookup"><span data-stu-id="9b655-105">This application does not demonstrate real world scenarios, such as using smart cards.</span></span> <span data-ttu-id="9b655-106">Zamiast tego pokazuje podstawowe informacje dotyczące szyfrowania i odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="9b655-106">Instead, it demonstrates the fundamentals of encryption and decryption.</span></span>  
  
 <span data-ttu-id="9b655-107">W tym instruktażu zastosowano następujące wytyczne dotyczące szyfrowania:</span><span class="sxs-lookup"><span data-stu-id="9b655-107">This walkthrough uses the following guidelines for encryption:</span></span>  
  
- <span data-ttu-id="9b655-108">Użyj klasy, algorytmu symetrycznego, aby szyfrować i odszyfrowywać dane przy użyciu automatycznie wygenerowanego <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A> <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A>i. <xref:System.Security.Cryptography.RijndaelManaged></span><span class="sxs-lookup"><span data-stu-id="9b655-108">Use the <xref:System.Security.Cryptography.RijndaelManaged> class, a symmetric algorithm, to encrypt and decrypt data by using its automatically generated <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> and <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>.</span></span>  
  
- <span data-ttu-id="9b655-109">Użyj algorytmu asymetrycznego, aby szyfrować i odszyfrowywać klucz do danych szyfrowanych przez <xref:System.Security.Cryptography.RijndaelManaged>program. <xref:System.Security.Cryptography.RSACryptoServiceProvider></span><span class="sxs-lookup"><span data-stu-id="9b655-109">Use the <xref:System.Security.Cryptography.RSACryptoServiceProvider>, an asymmetric algorithm, to encrypt and decrypt the key to the data encrypted by <xref:System.Security.Cryptography.RijndaelManaged>.</span></span> <span data-ttu-id="9b655-110">Algorytmy asymetryczne najlepiej używać w przypadku mniejszych ilości danych, takich jak klucz.</span><span class="sxs-lookup"><span data-stu-id="9b655-110">Asymmetric algorithms are best used for smaller amounts of data, such as a key.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="9b655-111">Jeśli chcesz chronić dane na komputerze zamiast wymieniać zaszyfrowaną zawartość z innymi osobami, rozważ użycie <xref:System.Security.Cryptography.ProtectedData> klas lub. <xref:System.Security.Cryptography.ProtectedMemory></span><span class="sxs-lookup"><span data-stu-id="9b655-111">If you want to protect data on your computer instead of exchanging encrypted content with other people, consider using the <xref:System.Security.Cryptography.ProtectedData> or <xref:System.Security.Cryptography.ProtectedMemory> classes.</span></span>  
  
 <span data-ttu-id="9b655-112">Poniższa tabela zawiera podsumowanie zadań kryptograficznych w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="9b655-112">The following table summarizes the cryptographic tasks in this topic.</span></span>  
  
|<span data-ttu-id="9b655-113">Zadanie</span><span class="sxs-lookup"><span data-stu-id="9b655-113">Task</span></span>|<span data-ttu-id="9b655-114">Opis</span><span class="sxs-lookup"><span data-stu-id="9b655-114">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="9b655-115">Tworzenie aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9b655-115">Creating a Windows Forms application</span></span>|<span data-ttu-id="9b655-116">Wyświetla listę kontrolek, które są wymagane do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9b655-116">Lists the controls that are required to run the application.</span></span>|  
|<span data-ttu-id="9b655-117">Deklarowanie obiektów globalnych</span><span class="sxs-lookup"><span data-stu-id="9b655-117">Declaring global objects</span></span>|<span data-ttu-id="9b655-118">Deklaruje zmienne ścieżki ciągów, <xref:System.Security.Cryptography.CspParameters> <xref:System.Security.Cryptography.RSACryptoServiceProvider> i i ma kontekst <xref:System.Windows.Forms.Form> globalny klasy.</span><span class="sxs-lookup"><span data-stu-id="9b655-118">Declares string path variables, the <xref:System.Security.Cryptography.CspParameters>, and the <xref:System.Security.Cryptography.RSACryptoServiceProvider> to have global context of the <xref:System.Windows.Forms.Form> class.</span></span>|  
|<span data-ttu-id="9b655-119">Tworzenie klucza asymetrycznego</span><span class="sxs-lookup"><span data-stu-id="9b655-119">Creating an asymmetric key</span></span>|<span data-ttu-id="9b655-120">Tworzy asymetryczną parę wartości klucza publicznego i prywatnego i przypisuje mu nazwę kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="9b655-120">Creates an asymmetric public and private key value pair and assigns it a key container name.</span></span>|  
|<span data-ttu-id="9b655-121">Szyfrowanie pliku</span><span class="sxs-lookup"><span data-stu-id="9b655-121">Encrypting a file</span></span>|<span data-ttu-id="9b655-122">Wyświetla okno dialogowe, w którym można wybrać plik do szyfrowania i szyfruje plik.</span><span class="sxs-lookup"><span data-stu-id="9b655-122">Displays a dialog box to select a file for encryption and encrypts the file.</span></span>|  
|<span data-ttu-id="9b655-123">Odszyfrowywanie pliku</span><span class="sxs-lookup"><span data-stu-id="9b655-123">Decrypting a file</span></span>|<span data-ttu-id="9b655-124">Wyświetla okno dialogowe, w którym można wybrać zaszyfrowany plik do odszyfrowania i odszyfrować plik.</span><span class="sxs-lookup"><span data-stu-id="9b655-124">Displays a dialog box to select an encrypted file for decryption and decrypts the file.</span></span>|  
|<span data-ttu-id="9b655-125">Pobieranie klucza prywatnego</span><span class="sxs-lookup"><span data-stu-id="9b655-125">Getting a private key</span></span>|<span data-ttu-id="9b655-126">Pobiera pełną parę kluczy przy użyciu nazwy kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="9b655-126">Gets the full key pair using the key container name.</span></span>|  
|<span data-ttu-id="9b655-127">Eksportowanie klucza publicznego</span><span class="sxs-lookup"><span data-stu-id="9b655-127">Exporting a public key</span></span>|<span data-ttu-id="9b655-128">Zapisuje klucz do pliku XML tylko z parametrami publicznymi.</span><span class="sxs-lookup"><span data-stu-id="9b655-128">Saves the key to an XML file with only public parameters.</span></span>|  
|<span data-ttu-id="9b655-129">Importowanie klucza publicznego</span><span class="sxs-lookup"><span data-stu-id="9b655-129">Importing a public key</span></span>|<span data-ttu-id="9b655-130">Ładuje klucz z pliku XML do kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="9b655-130">Loads the key from an XML file into the key container.</span></span>|  
|<span data-ttu-id="9b655-131">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="9b655-131">Testing the application</span></span>|<span data-ttu-id="9b655-132">Wyświetla listę procedur testowania tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9b655-132">Lists procedures for testing this application.</span></span>|  
  
## <a name="prerequisites"></a><span data-ttu-id="9b655-133">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="9b655-133">Prerequisites</span></span>  
 <span data-ttu-id="9b655-134">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="9b655-134">You need the following components to complete this walkthrough:</span></span>  
  
- <span data-ttu-id="9b655-135">Odwołania do <xref:System.IO> przestrzeni nazw <xref:System.Security.Cryptography> i.</span><span class="sxs-lookup"><span data-stu-id="9b655-135">References to the <xref:System.IO> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
## <a name="creating-a-windows-forms-application"></a><span data-ttu-id="9b655-136">Tworzenie aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9b655-136">Creating a Windows Forms Application</span></span>  
 <span data-ttu-id="9b655-137">Większość przykładów kodu w tym instruktażu została zaprojektowana jako programy obsługi zdarzeń dla kontrolek Button.</span><span class="sxs-lookup"><span data-stu-id="9b655-137">Most of the code examples in this walkthrough are designed to be event handlers for button controls.</span></span> <span data-ttu-id="9b655-138">Poniższa tabela zawiera listę formantów wymaganych dla przykładowej aplikacji i ich wymaganych nazw w celu dopasowania do przykładów kodu.</span><span class="sxs-lookup"><span data-stu-id="9b655-138">The following table lists the controls required for the sample application and their required names to match the code examples.</span></span>  
  
|<span data-ttu-id="9b655-139">formant</span><span class="sxs-lookup"><span data-stu-id="9b655-139">Control</span></span>|<span data-ttu-id="9b655-140">Nazwa</span><span class="sxs-lookup"><span data-stu-id="9b655-140">Name</span></span>|<span data-ttu-id="9b655-141">Właściwość Text (zgodnie z wymaganiami)</span><span class="sxs-lookup"><span data-stu-id="9b655-141">Text property (as needed)</span></span>|  
|-------------|----------|---------------------------------|  
|<xref:System.Windows.Forms.Button>|`buttonEncryptFile`|<span data-ttu-id="9b655-142">Szyfruj plik</span><span class="sxs-lookup"><span data-stu-id="9b655-142">Encrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonDecryptFile`|<span data-ttu-id="9b655-143">Odszyfruj plik</span><span class="sxs-lookup"><span data-stu-id="9b655-143">Decrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonCreateAsmKeys`|<span data-ttu-id="9b655-144">Utwórz klucze</span><span class="sxs-lookup"><span data-stu-id="9b655-144">Create Keys</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonExportPublicKey`|<span data-ttu-id="9b655-145">Eksportuj klucz publiczny</span><span class="sxs-lookup"><span data-stu-id="9b655-145">Export Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonImportPublicKey`|<span data-ttu-id="9b655-146">Importuj klucz publiczny</span><span class="sxs-lookup"><span data-stu-id="9b655-146">Import Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonGetPrivateKey`|<span data-ttu-id="9b655-147">Pobierz klucz prywatny</span><span class="sxs-lookup"><span data-stu-id="9b655-147">Get Private Key</span></span>|  
|<xref:System.Windows.Forms.Label>|`label1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog2`||  
  
 <span data-ttu-id="9b655-148">Kliknij dwukrotnie przyciski w projektancie programu Visual Studio, aby utworzyć obsługę zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="9b655-148">Double-click the buttons in the  Visual Studio designer to create their event handlers.</span></span>  
  
## <a name="declaring-global-objects"></a><span data-ttu-id="9b655-149">Deklarowanie obiektów globalnych</span><span class="sxs-lookup"><span data-stu-id="9b655-149">Declaring Global Objects</span></span>  
 <span data-ttu-id="9b655-150">Dodaj następujący kod do konstruktora formularza.</span><span class="sxs-lookup"><span data-stu-id="9b655-150">Add the following code to the Form's constructor.</span></span> <span data-ttu-id="9b655-151">Edytuj zmienne ciągów dla środowiska i preferencji.</span><span class="sxs-lookup"><span data-stu-id="9b655-151">Edit the string variables for your environment and preferences.</span></span>  
  
 [!code-csharp[CryptoWalkThru#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#1)]
 [!code-vb[CryptoWalkThru#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#1)]  
  
## <a name="creating-an-asymmetric-key"></a><span data-ttu-id="9b655-152">Tworzenie klucza asymetrycznego</span><span class="sxs-lookup"><span data-stu-id="9b655-152">Creating an Asymmetric Key</span></span>  
 <span data-ttu-id="9b655-153">To zadanie tworzy klucz asymetryczny, który szyfruje i odszyfrowuje <xref:System.Security.Cryptography.RijndaelManaged> klucz.</span><span class="sxs-lookup"><span data-stu-id="9b655-153">This task creates an asymmetric key that encrypts and decrypts the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span> <span data-ttu-id="9b655-154">Ten klucz został użyty do zaszyfrowania zawartości i wyświetla nazwę kontenera kluczy w kontrolce etykieta.</span><span class="sxs-lookup"><span data-stu-id="9b655-154">This key was used to encrypt the content and it displays the key container name on the label control.</span></span>  
  
 <span data-ttu-id="9b655-155">Dodaj następujący kod jako `Click` procedurę obsługi zdarzeń `Create Keys` dla przycisku (`buttonCreateAsmKeys_Click`).</span><span class="sxs-lookup"><span data-stu-id="9b655-155">Add the following code as the `Click` event handler for the `Create Keys` button (`buttonCreateAsmKeys_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#2)]
 [!code-vb[CryptoWalkThru#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#2)]  
  
## <a name="encrypting-a-file"></a><span data-ttu-id="9b655-156">Szyfrowanie pliku</span><span class="sxs-lookup"><span data-stu-id="9b655-156">Encrypting a File</span></span>  
 <span data-ttu-id="9b655-157">To zadanie obejmuje dwie metody: metoda obsługi zdarzeń dla `Encrypt File` przycisku (`buttonEncryptFile_Click`) i `EncryptFile` metody.</span><span class="sxs-lookup"><span data-stu-id="9b655-157">This task involves two methods: the event handler method for the `Encrypt File` button (`buttonEncryptFile_Click`) and the `EncryptFile` method.</span></span> <span data-ttu-id="9b655-158">Pierwsza metoda wyświetla okno dialogowe, w którym można wybrać plik i przekazuje nazwę pliku do drugiej metody, która wykonuje szyfrowanie.</span><span class="sxs-lookup"><span data-stu-id="9b655-158">The first method displays a dialog box for selecting a file and passes the file name to the second method, which performs the encryption.</span></span>  
  
 <span data-ttu-id="9b655-159">Zaszyfrowana zawartość, klucz i IV są zapisywane na jednym <xref:System.IO.FileStream>, który jest nazywany Pakietem szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="9b655-159">The encrypted content, key, and IV are all saved to one <xref:System.IO.FileStream>, which is referred to as the encryption package.</span></span>  
  
 <span data-ttu-id="9b655-160">`EncryptFile` Metoda wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="9b655-160">The `EncryptFile` method does the following:</span></span>  
  
1. <span data-ttu-id="9b655-161">Tworzy algorytm <xref:System.Security.Cryptography.RijndaelManaged> symetryczny do szyfrowania zawartości.</span><span class="sxs-lookup"><span data-stu-id="9b655-161">Creates a <xref:System.Security.Cryptography.RijndaelManaged> symmetric algorithm to encrypt the content.</span></span>  
  
2. <span data-ttu-id="9b655-162">Tworzy obiekt służący do <xref:System.Security.Cryptography.RijndaelManaged> szyfrowania klucza. <xref:System.Security.Cryptography.RSACryptoServiceProvider></span><span class="sxs-lookup"><span data-stu-id="9b655-162">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to encrypt the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span>  
  
3. <span data-ttu-id="9b655-163">Używa obiektu do odczytu i <xref:System.IO.FileStream> szyfrowania pliku źródłowego w blokach bajtów do obiektu docelowego <xref:System.IO.FileStream> dla zaszyfrowanego pliku. <xref:System.Security.Cryptography.CryptoStream></span><span class="sxs-lookup"><span data-stu-id="9b655-163">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and encrypt the <xref:System.IO.FileStream> of the source file, in blocks of bytes, into a destination <xref:System.IO.FileStream> object for the encrypted file.</span></span>  
  
4. <span data-ttu-id="9b655-164">Określa długość zaszyfrowanego klucza i IV i tworzy tablicę bajtową wartości ich długości.</span><span class="sxs-lookup"><span data-stu-id="9b655-164">Determines the lengths of the encrypted key and IV, and creates byte arrays of their length values.</span></span>  
  
5. <span data-ttu-id="9b655-165">Zapisuje wartości key, IV i ich długości do zaszyfrowanego pakietu.</span><span class="sxs-lookup"><span data-stu-id="9b655-165">Writes the Key, IV, and their length values to the encrypted package.</span></span>  
  
 <span data-ttu-id="9b655-166">Pakiet szyfrowania używa następującego formatu:</span><span class="sxs-lookup"><span data-stu-id="9b655-166">The encryption package uses the following format:</span></span>  
  
- <span data-ttu-id="9b655-167">Długość klucza, bajty 0-3</span><span class="sxs-lookup"><span data-stu-id="9b655-167">Key length, bytes 0 - 3</span></span>  
  
- <span data-ttu-id="9b655-168">Długość IV, bajtów 4-7</span><span class="sxs-lookup"><span data-stu-id="9b655-168">IV length, bytes 4 - 7</span></span>  
  
- <span data-ttu-id="9b655-169">Zaszyfrowany klucz</span><span class="sxs-lookup"><span data-stu-id="9b655-169">Encrypted key</span></span>  
  
- <span data-ttu-id="9b655-170">IV</span><span class="sxs-lookup"><span data-stu-id="9b655-170">IV</span></span>  
  
- <span data-ttu-id="9b655-171">Szyfrowanie tekstu</span><span class="sxs-lookup"><span data-stu-id="9b655-171">Cipher text</span></span>  
  
 <span data-ttu-id="9b655-172">Możesz użyć długości klucza i IV, aby określić punkty początkowe i długości wszystkich części pakietu szyfrującego, które mogą być następnie użyte do odszyfrowania pliku.</span><span class="sxs-lookup"><span data-stu-id="9b655-172">You can use the lengths of the key and IV to determine the starting points and lengths of all parts of the encryption package, which can then be used to decrypt the file.</span></span>  
  
 <span data-ttu-id="9b655-173">Dodaj następujący kod jako `Click` procedurę obsługi zdarzeń `Encrypt File` dla przycisku (`buttonEncryptFile_Click`).</span><span class="sxs-lookup"><span data-stu-id="9b655-173">Add the following code as the `Click` event handler for the `Encrypt File` button (`buttonEncryptFile_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#3)]
 [!code-vb[CryptoWalkThru#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#3)]  
  
 <span data-ttu-id="9b655-174">Dodaj następującą `EncryptFile` metodę do formularza.</span><span class="sxs-lookup"><span data-stu-id="9b655-174">Add the following `EncryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#5)]
 [!code-vb[CryptoWalkThru#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#5)]  
  
## <a name="decrypting-a-file"></a><span data-ttu-id="9b655-175">Odszyfrowywanie pliku</span><span class="sxs-lookup"><span data-stu-id="9b655-175">Decrypting a File</span></span>  
 <span data-ttu-id="9b655-176">To zadanie obejmuje dwie metody, metodę obsługi zdarzeń dla `Decrypt File` przycisku (`buttonDecryptFile_Click`) i `DecryptFile` metodę.</span><span class="sxs-lookup"><span data-stu-id="9b655-176">This task involves two methods, the event handler method for the `Decrypt File` button (`buttonDecryptFile_Click`), and the `DecryptFile` method.</span></span> <span data-ttu-id="9b655-177">Pierwsza metoda wyświetla okno dialogowe, w którym można wybrać plik i przekazuje jego nazwę pliku do drugiej metody, która wykonuje odszyfrowywanie.</span><span class="sxs-lookup"><span data-stu-id="9b655-177">The first method displays a dialog box for selecting a file and passes its file name to the second method, which performs the decryption.</span></span>  
  
 <span data-ttu-id="9b655-178">`Decrypt` Metoda wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="9b655-178">The `Decrypt` method does the following:</span></span>  
  
1. <span data-ttu-id="9b655-179">Tworzy algorytm <xref:System.Security.Cryptography.RijndaelManaged> symetryczny służący do odszyfrowywania zawartości.</span><span class="sxs-lookup"><span data-stu-id="9b655-179">Creates a <xref:System.Security.Cryptography.RijndaelManaged> symmetric algorithm to decrypt the content.</span></span>  
  
2. <span data-ttu-id="9b655-180">Odczytuje pierwsze osiem bajtów <xref:System.IO.FileStream> zaszyfrowanego pakietu do tablic bajtów w celu uzyskania długości zaszyfrowanego klucza i IV.</span><span class="sxs-lookup"><span data-stu-id="9b655-180">Reads the first eight bytes of the <xref:System.IO.FileStream> of the encrypted package into byte arrays to obtain the lengths of the encrypted key and the IV.</span></span>  
  
3. <span data-ttu-id="9b655-181">Wyodrębnia klucz i IV z pakietu szyfrowania do tablic bajtowych.</span><span class="sxs-lookup"><span data-stu-id="9b655-181">Extracts the key and IV from the encryption package into byte arrays.</span></span>  
  
4. <span data-ttu-id="9b655-182">Tworzy obiekt do odszyfrowania <xref:System.Security.Cryptography.RijndaelManaged>klucza. <xref:System.Security.Cryptography.RSACryptoServiceProvider></span><span class="sxs-lookup"><span data-stu-id="9b655-182">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to decrypt the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span>  
  
5. <span data-ttu-id="9b655-183">Używa obiektu do odczytywania i odszyfrowywania sekcji <xref:System.IO.FileStream> szyfrowania tekstu pakietu szyfrowania w blokach bajtów do <xref:System.IO.FileStream> obiektu w odszyfrowanym pliku. <xref:System.Security.Cryptography.CryptoStream></span><span class="sxs-lookup"><span data-stu-id="9b655-183">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and decrypt the cipher text section of the <xref:System.IO.FileStream> encryption package, in blocks of bytes, into the <xref:System.IO.FileStream> object for the decrypted file.</span></span> <span data-ttu-id="9b655-184">Po zakończeniu odszyfrowywania zostanie zakończone.</span><span class="sxs-lookup"><span data-stu-id="9b655-184">When this is finished, the decryption is completed.</span></span>  
  
 <span data-ttu-id="9b655-185">Dodaj następujący kod jako `Click` procedurę obsługi zdarzeń `Decrypt File` dla przycisku.</span><span class="sxs-lookup"><span data-stu-id="9b655-185">Add the following code as the `Click` event handler for the `Decrypt File` button.</span></span>  
  
 [!code-csharp[CryptoWalkThru#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#4)]
 [!code-vb[CryptoWalkThru#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#4)]  
  
 <span data-ttu-id="9b655-186">Dodaj następującą `DecryptFile` metodę do formularza.</span><span class="sxs-lookup"><span data-stu-id="9b655-186">Add the following `DecryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#6)]
 [!code-vb[CryptoWalkThru#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#6)]  
  
## <a name="exporting-a-public-key"></a><span data-ttu-id="9b655-187">Eksportowanie klucza publicznego</span><span class="sxs-lookup"><span data-stu-id="9b655-187">Exporting a Public Key</span></span>  
 <span data-ttu-id="9b655-188">To zadanie służy do zapisywania klucza utworzonego przez `Create Keys` przycisk do pliku.</span><span class="sxs-lookup"><span data-stu-id="9b655-188">This task saves the key created by the `Create Keys` button to a file.</span></span> <span data-ttu-id="9b655-189">Eksportuje tylko parametry publiczne.</span><span class="sxs-lookup"><span data-stu-id="9b655-189">It exports only the public parameters.</span></span>  
  
 <span data-ttu-id="9b655-190">To zadanie symuluje scenariusz dla Alicja przekazującej Roberta swój klucz publiczny, aby mógł szyfrować pliki.</span><span class="sxs-lookup"><span data-stu-id="9b655-190">This task simulates the scenario of Alice giving Bob her public key so that he can encrypt files for her.</span></span> <span data-ttu-id="9b655-191">Osoby, które mają ten klucz publiczny, nie będą w stanie odszyfrować, ponieważ nie mają pełnej pary kluczy z parametrami prywatnymi.</span><span class="sxs-lookup"><span data-stu-id="9b655-191">He and others who have that public key will not be able to decrypt them because they do not have the full key pair with private parameters.</span></span>  
  
 <span data-ttu-id="9b655-192">Dodaj następujący kod jako `Click` procedurę obsługi zdarzeń `Export Public Key` dla przycisku (`buttonExportPublicKey_Click`).</span><span class="sxs-lookup"><span data-stu-id="9b655-192">Add the following code as the `Click` event handler for the `Export Public Key` button (`buttonExportPublicKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#8)]
 [!code-vb[CryptoWalkThru#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#8)]  
  
## <a name="importing-a-public-key"></a><span data-ttu-id="9b655-193">Importowanie klucza publicznego</span><span class="sxs-lookup"><span data-stu-id="9b655-193">Importing a Public Key</span></span>  
 <span data-ttu-id="9b655-194">To zadanie ładuje klucz z tylko parametrami publicznymi, utworzonym przez `Export Public Key` przycisk i ustawia go jako nazwę kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="9b655-194">This task loads the key with only public parameters, as created by the `Export Public Key` button, and sets it as the key container name.</span></span>  
  
 <span data-ttu-id="9b655-195">To zadanie symuluje scenariusz ładowania klucza Alicja z tylko parametrami publicznymi, dzięki czemu może zaszyfrować pliki.</span><span class="sxs-lookup"><span data-stu-id="9b655-195">This task simulates the scenario of Bob loading Alice's key with only public parameters so he can encrypt files for her.</span></span>  
  
 <span data-ttu-id="9b655-196">Dodaj następujący kod jako `Click` procedurę obsługi zdarzeń `Import Public Key` dla przycisku (`buttonImportPublicKey_Click`).</span><span class="sxs-lookup"><span data-stu-id="9b655-196">Add the following code as the `Click` event handler for the `Import Public Key` button (`buttonImportPublicKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#9)]
 [!code-vb[CryptoWalkThru#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#9)]  
  
## <a name="getting-a-private-key"></a><span data-ttu-id="9b655-197">Pobieranie klucza prywatnego</span><span class="sxs-lookup"><span data-stu-id="9b655-197">Getting a Private Key</span></span>  
 <span data-ttu-id="9b655-198">To zadanie ustawia nazwę kontenera kluczy na nazwę klucza utworzonego za pomocą `Create Keys` przycisku.</span><span class="sxs-lookup"><span data-stu-id="9b655-198">This task sets the key container name to the name of the key created by using the `Create Keys` button.</span></span> <span data-ttu-id="9b655-199">Kontener kluczy będzie zawierać pełną parę kluczy z parametrami prywatnymi.</span><span class="sxs-lookup"><span data-stu-id="9b655-199">The key container will contain the full key pair with private parameters.</span></span>  
  
 <span data-ttu-id="9b655-200">To zadanie symuluje scenariusz Alicja przy użyciu klucza prywatnego w celu odszyfrowania plików zaszyfrowanych przez Robert.</span><span class="sxs-lookup"><span data-stu-id="9b655-200">This task simulates the scenario of Alice using her private key to decrypt files encrypted by Bob.</span></span>  
  
 <span data-ttu-id="9b655-201">Dodaj następujący kod jako `Click` procedurę obsługi zdarzeń `Get Private Key` dla przycisku (`buttonGetPrivateKey_Click`).</span><span class="sxs-lookup"><span data-stu-id="9b655-201">Add the following code as the `Click` event handler for the `Get Private Key` button (`buttonGetPrivateKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#7)]
 [!code-vb[CryptoWalkThru#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#7)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="9b655-202">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="9b655-202">Testing the Application</span></span>  
 <span data-ttu-id="9b655-203">Po skompilowaniu aplikacji wykonaj następujące scenariusze testowania.</span><span class="sxs-lookup"><span data-stu-id="9b655-203">After you have built the application, perform the following testing scenarios.</span></span>  
  
#### <a name="to-create-keys-encrypt-and-decrypt"></a><span data-ttu-id="9b655-204">Aby utworzyć klucze, szyfrowanie i odszyfrowywanie</span><span class="sxs-lookup"><span data-stu-id="9b655-204">To create keys, encrypt, and decrypt</span></span>  
  
1. <span data-ttu-id="9b655-205">`Create Keys` Kliknij przycisk.</span><span class="sxs-lookup"><span data-stu-id="9b655-205">Click the `Create Keys` button.</span></span> <span data-ttu-id="9b655-206">Etykieta Wyświetla nazwę klucza i pokazuje, że jest to pełna para kluczy.</span><span class="sxs-lookup"><span data-stu-id="9b655-206">The label displays the key name and shows that it is a full key pair.</span></span>  
  
2. <span data-ttu-id="9b655-207">`Export Public Key` Kliknij przycisk.</span><span class="sxs-lookup"><span data-stu-id="9b655-207">Click the `Export Public Key` button.</span></span> <span data-ttu-id="9b655-208">Należy zauważyć, że eksportowanie parametrów klucza publicznego nie zmienia bieżącego klucza.</span><span class="sxs-lookup"><span data-stu-id="9b655-208">Note that exporting the public key parameters does not change the current key.</span></span>  
  
3. <span data-ttu-id="9b655-209">`Encrypt File` Kliknij przycisk i wybierz plik.</span><span class="sxs-lookup"><span data-stu-id="9b655-209">Click the `Encrypt File` button and select a file.</span></span>  
  
4. <span data-ttu-id="9b655-210">`Decrypt File` Kliknij przycisk i wybierz plik, który został zaszyfrowany.</span><span class="sxs-lookup"><span data-stu-id="9b655-210">Click the `Decrypt File` button and select the file just encrypted.</span></span>  
  
5. <span data-ttu-id="9b655-211">Zapoznaj się z odszyfrowaniem pliku.</span><span class="sxs-lookup"><span data-stu-id="9b655-211">Examine the file just decrypted.</span></span>  
  
6. <span data-ttu-id="9b655-212">Zamknij aplikację i uruchom ją ponownie, aby przetestować pobieranie utrwalonych kontenerów kluczy w następnym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="9b655-212">Close the application and restart it to test retrieving persisted key containers in the next scenario.</span></span>  
  
#### <a name="to-encrypt-using-the-public-key"></a><span data-ttu-id="9b655-213">Aby zaszyfrować przy użyciu klucza publicznego</span><span class="sxs-lookup"><span data-stu-id="9b655-213">To encrypt using the public key</span></span>  
  
1. <span data-ttu-id="9b655-214">`Import Public Key` Kliknij przycisk.</span><span class="sxs-lookup"><span data-stu-id="9b655-214">Click the `Import Public Key` button.</span></span> <span data-ttu-id="9b655-215">Etykieta Wyświetla nazwę klucza i pokazuje, że jest tylko publiczna.</span><span class="sxs-lookup"><span data-stu-id="9b655-215">The label displays the key name and shows that it is public only.</span></span>  
  
2. <span data-ttu-id="9b655-216">`Encrypt File` Kliknij przycisk i wybierz plik.</span><span class="sxs-lookup"><span data-stu-id="9b655-216">Click the `Encrypt File` button and select a file.</span></span>  
  
3. <span data-ttu-id="9b655-217">`Decrypt File` Kliknij przycisk i wybierz plik, który został zaszyfrowany.</span><span class="sxs-lookup"><span data-stu-id="9b655-217">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="9b655-218">Nie powiedzie się, ponieważ musisz mieć klucz prywatny do odszyfrowania.</span><span class="sxs-lookup"><span data-stu-id="9b655-218">This will fail because you must have the private key to decrypt.</span></span>  
  
 <span data-ttu-id="9b655-219">W tym scenariuszu przedstawiono tylko klucz publiczny do szyfrowania pliku dla innej osoby.</span><span class="sxs-lookup"><span data-stu-id="9b655-219">This scenario demonstrates having only the public key to encrypt a file for another person.</span></span> <span data-ttu-id="9b655-220">Zwykle osoba ta może uzyskać tylko klucz publiczny i wstrzymać klucz prywatny do odszyfrowania.</span><span class="sxs-lookup"><span data-stu-id="9b655-220">Typically that person would give you only the public key and withhold the private key for decryption.</span></span>  
  
#### <a name="to-decrypt-using-the-private-key"></a><span data-ttu-id="9b655-221">Aby odszyfrować przy użyciu klucza prywatnego</span><span class="sxs-lookup"><span data-stu-id="9b655-221">To decrypt using the private key</span></span>  
  
1. <span data-ttu-id="9b655-222">`Get Private Key` Kliknij przycisk.</span><span class="sxs-lookup"><span data-stu-id="9b655-222">Click the `Get Private Key` button.</span></span> <span data-ttu-id="9b655-223">Etykieta Wyświetla nazwę klucza i pokazuje, czy jest to pełna para kluczy.</span><span class="sxs-lookup"><span data-stu-id="9b655-223">The label displays the key name and shows whether it is the full key pair.</span></span>  
  
2. <span data-ttu-id="9b655-224">`Decrypt File` Kliknij przycisk i wybierz plik, który został zaszyfrowany.</span><span class="sxs-lookup"><span data-stu-id="9b655-224">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="9b655-225">Ta operacja zakończy się pomyślnie, ponieważ masz pełną parę kluczy do odszyfrowania.</span><span class="sxs-lookup"><span data-stu-id="9b655-225">This will be successful because you have the full key pair to decrypt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b655-226">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9b655-226">See also</span></span>

- [<span data-ttu-id="9b655-227">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="9b655-227">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
