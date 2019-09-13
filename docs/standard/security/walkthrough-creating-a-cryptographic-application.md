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
ms.openlocfilehash: ee6dafa8578c59d23908bf0e184091bb4ceaeb45
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895288"
---
# <a name="walkthrough-creating-a-cryptographic-application"></a><span data-ttu-id="08b2b-102">Przewodnik: Tworzenie aplikacji kryptograficznej</span><span class="sxs-lookup"><span data-stu-id="08b2b-102">Walkthrough: Creating a Cryptographic Application</span></span>
<span data-ttu-id="08b2b-103">W tym instruktażu pokazano, jak szyfrować i odszyfrowywać zawartość.</span><span class="sxs-lookup"><span data-stu-id="08b2b-103">This walkthrough demonstrates how to encrypt and decrypt content.</span></span> <span data-ttu-id="08b2b-104">Przykłady kodu są przeznaczone dla aplikacji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="08b2b-104">The code examples are designed for a Windows Forms application.</span></span> <span data-ttu-id="08b2b-105">Ta aplikacja nie pokazuje rzeczywistych scenariuszy, takich jak korzystanie z kart inteligentnych.</span><span class="sxs-lookup"><span data-stu-id="08b2b-105">This application does not demonstrate real world scenarios, such as using smart cards.</span></span> <span data-ttu-id="08b2b-106">Zamiast tego pokazuje podstawowe informacje dotyczące szyfrowania i odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="08b2b-106">Instead, it demonstrates the fundamentals of encryption and decryption.</span></span>  
  
 <span data-ttu-id="08b2b-107">W tym instruktażu zastosowano następujące wytyczne dotyczące szyfrowania:</span><span class="sxs-lookup"><span data-stu-id="08b2b-107">This walkthrough uses the following guidelines for encryption:</span></span>  
  
- <span data-ttu-id="08b2b-108">Użyj klasy, algorytmu symetrycznego, aby szyfrować i odszyfrowywać dane przy użyciu automatycznie wygenerowanego <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A> <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A>i. <xref:System.Security.Cryptography.RijndaelManaged></span><span class="sxs-lookup"><span data-stu-id="08b2b-108">Use the <xref:System.Security.Cryptography.RijndaelManaged> class, a symmetric algorithm, to encrypt and decrypt data by using its automatically generated <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> and <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>.</span></span>  
  
- <span data-ttu-id="08b2b-109">Użyj algorytmu asymetrycznego, aby szyfrować i odszyfrowywać klucz do danych szyfrowanych przez <xref:System.Security.Cryptography.RijndaelManaged>program. <xref:System.Security.Cryptography.RSACryptoServiceProvider></span><span class="sxs-lookup"><span data-stu-id="08b2b-109">Use the <xref:System.Security.Cryptography.RSACryptoServiceProvider>, an asymmetric algorithm, to encrypt and decrypt the key to the data encrypted by <xref:System.Security.Cryptography.RijndaelManaged>.</span></span> <span data-ttu-id="08b2b-110">Algorytmy asymetryczne najlepiej używać w przypadku mniejszych ilości danych, takich jak klucz.</span><span class="sxs-lookup"><span data-stu-id="08b2b-110">Asymmetric algorithms are best used for smaller amounts of data, such as a key.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="08b2b-111">Jeśli chcesz chronić dane na komputerze zamiast wymieniać zaszyfrowaną zawartość z innymi osobami, rozważ użycie <xref:System.Security.Cryptography.ProtectedData> klas lub. <xref:System.Security.Cryptography.ProtectedMemory></span><span class="sxs-lookup"><span data-stu-id="08b2b-111">If you want to protect data on your computer instead of exchanging encrypted content with other people, consider using the <xref:System.Security.Cryptography.ProtectedData> or <xref:System.Security.Cryptography.ProtectedMemory> classes.</span></span>  
  
 <span data-ttu-id="08b2b-112">Poniższa tabela zawiera podsumowanie zadań kryptograficznych w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="08b2b-112">The following table summarizes the cryptographic tasks in this topic.</span></span>  
  
|<span data-ttu-id="08b2b-113">Zadanie</span><span class="sxs-lookup"><span data-stu-id="08b2b-113">Task</span></span>|<span data-ttu-id="08b2b-114">Opis</span><span class="sxs-lookup"><span data-stu-id="08b2b-114">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="08b2b-115">Tworzenie aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="08b2b-115">Creating a Windows Forms application</span></span>|<span data-ttu-id="08b2b-116">Wyświetla listę kontrolek, które są wymagane do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="08b2b-116">Lists the controls that are required to run the application.</span></span>|  
|<span data-ttu-id="08b2b-117">Deklarowanie obiektów globalnych</span><span class="sxs-lookup"><span data-stu-id="08b2b-117">Declaring global objects</span></span>|<span data-ttu-id="08b2b-118">Deklaruje zmienne ścieżki ciągów, <xref:System.Security.Cryptography.CspParameters> <xref:System.Security.Cryptography.RSACryptoServiceProvider> i i ma kontekst <xref:System.Windows.Forms.Form> globalny klasy.</span><span class="sxs-lookup"><span data-stu-id="08b2b-118">Declares string path variables, the <xref:System.Security.Cryptography.CspParameters>, and the <xref:System.Security.Cryptography.RSACryptoServiceProvider> to have global context of the <xref:System.Windows.Forms.Form> class.</span></span>|  
|<span data-ttu-id="08b2b-119">Tworzenie klucza asymetrycznego</span><span class="sxs-lookup"><span data-stu-id="08b2b-119">Creating an asymmetric key</span></span>|<span data-ttu-id="08b2b-120">Tworzy asymetryczną parę wartości klucza publicznego i prywatnego i przypisuje mu nazwę kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="08b2b-120">Creates an asymmetric public and private key value pair and assigns it a key container name.</span></span>|  
|<span data-ttu-id="08b2b-121">Szyfrowanie pliku</span><span class="sxs-lookup"><span data-stu-id="08b2b-121">Encrypting a file</span></span>|<span data-ttu-id="08b2b-122">Wyświetla okno dialogowe, w którym można wybrać plik do szyfrowania i szyfruje plik.</span><span class="sxs-lookup"><span data-stu-id="08b2b-122">Displays a dialog box to select a file for encryption and encrypts the file.</span></span>|  
|<span data-ttu-id="08b2b-123">Odszyfrowywanie pliku</span><span class="sxs-lookup"><span data-stu-id="08b2b-123">Decrypting a file</span></span>|<span data-ttu-id="08b2b-124">Wyświetla okno dialogowe, w którym można wybrać zaszyfrowany plik do odszyfrowania i odszyfrować plik.</span><span class="sxs-lookup"><span data-stu-id="08b2b-124">Displays a dialog box to select an encrypted file for decryption and decrypts the file.</span></span>|  
|<span data-ttu-id="08b2b-125">Pobieranie klucza prywatnego</span><span class="sxs-lookup"><span data-stu-id="08b2b-125">Getting a private key</span></span>|<span data-ttu-id="08b2b-126">Pobiera pełną parę kluczy przy użyciu nazwy kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="08b2b-126">Gets the full key pair using the key container name.</span></span>|  
|<span data-ttu-id="08b2b-127">Eksportowanie klucza publicznego</span><span class="sxs-lookup"><span data-stu-id="08b2b-127">Exporting a public key</span></span>|<span data-ttu-id="08b2b-128">Zapisuje klucz do pliku XML tylko z parametrami publicznymi.</span><span class="sxs-lookup"><span data-stu-id="08b2b-128">Saves the key to an XML file with only public parameters.</span></span>|  
|<span data-ttu-id="08b2b-129">Importowanie klucza publicznego</span><span class="sxs-lookup"><span data-stu-id="08b2b-129">Importing a public key</span></span>|<span data-ttu-id="08b2b-130">Ładuje klucz z pliku XML do kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="08b2b-130">Loads the key from an XML file into the key container.</span></span>|  
|<span data-ttu-id="08b2b-131">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="08b2b-131">Testing the application</span></span>|<span data-ttu-id="08b2b-132">Wyświetla listę procedur testowania tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="08b2b-132">Lists procedures for testing this application.</span></span>|  
  
## <a name="prerequisites"></a><span data-ttu-id="08b2b-133">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="08b2b-133">Prerequisites</span></span>  
 <span data-ttu-id="08b2b-134">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="08b2b-134">You need the following components to complete this walkthrough:</span></span>  
  
- <span data-ttu-id="08b2b-135">Odwołania do <xref:System.IO> przestrzeni nazw <xref:System.Security.Cryptography> i.</span><span class="sxs-lookup"><span data-stu-id="08b2b-135">References to the <xref:System.IO> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
## <a name="creating-a-windows-forms-application"></a><span data-ttu-id="08b2b-136">Tworzenie aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="08b2b-136">Creating a Windows Forms Application</span></span>  
 <span data-ttu-id="08b2b-137">Większość przykładów kodu w tym instruktażu została zaprojektowana jako programy obsługi zdarzeń dla kontrolek Button.</span><span class="sxs-lookup"><span data-stu-id="08b2b-137">Most of the code examples in this walkthrough are designed to be event handlers for button controls.</span></span> <span data-ttu-id="08b2b-138">Poniższa tabela zawiera listę formantów wymaganych dla przykładowej aplikacji i ich wymaganych nazw w celu dopasowania do przykładów kodu.</span><span class="sxs-lookup"><span data-stu-id="08b2b-138">The following table lists the controls required for the sample application and their required names to match the code examples.</span></span>  
  
|<span data-ttu-id="08b2b-139">formant</span><span class="sxs-lookup"><span data-stu-id="08b2b-139">Control</span></span>|<span data-ttu-id="08b2b-140">Nazwa</span><span class="sxs-lookup"><span data-stu-id="08b2b-140">Name</span></span>|<span data-ttu-id="08b2b-141">Właściwość Text (zgodnie z wymaganiami)</span><span class="sxs-lookup"><span data-stu-id="08b2b-141">Text property (as needed)</span></span>|  
|-------------|----------|---------------------------------|  
|<xref:System.Windows.Forms.Button>|`buttonEncryptFile`|<span data-ttu-id="08b2b-142">Szyfruj plik</span><span class="sxs-lookup"><span data-stu-id="08b2b-142">Encrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonDecryptFile`|<span data-ttu-id="08b2b-143">Odszyfruj plik</span><span class="sxs-lookup"><span data-stu-id="08b2b-143">Decrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonCreateAsmKeys`|<span data-ttu-id="08b2b-144">Utwórz klucze</span><span class="sxs-lookup"><span data-stu-id="08b2b-144">Create Keys</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonExportPublicKey`|<span data-ttu-id="08b2b-145">Eksportuj klucz publiczny</span><span class="sxs-lookup"><span data-stu-id="08b2b-145">Export Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonImportPublicKey`|<span data-ttu-id="08b2b-146">Importuj klucz publiczny</span><span class="sxs-lookup"><span data-stu-id="08b2b-146">Import Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonGetPrivateKey`|<span data-ttu-id="08b2b-147">Pobierz klucz prywatny</span><span class="sxs-lookup"><span data-stu-id="08b2b-147">Get Private Key</span></span>|  
|<xref:System.Windows.Forms.Label>|`label1`|<span data-ttu-id="08b2b-148">Nie ustawiono klucza</span><span class="sxs-lookup"><span data-stu-id="08b2b-148">Key not set</span></span>|  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog2`||  
  
 <span data-ttu-id="08b2b-149">Kliknij dwukrotnie przyciski w projektancie programu Visual Studio, aby utworzyć obsługę zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="08b2b-149">Double-click the buttons in the  Visual Studio designer to create their event handlers.</span></span>  
  
## <a name="declaring-global-objects"></a><span data-ttu-id="08b2b-150">Deklarowanie obiektów globalnych</span><span class="sxs-lookup"><span data-stu-id="08b2b-150">Declaring Global Objects</span></span>  
 <span data-ttu-id="08b2b-151">Dodaj następujący kod do konstruktora formularza.</span><span class="sxs-lookup"><span data-stu-id="08b2b-151">Add the following code to the Form's constructor.</span></span> <span data-ttu-id="08b2b-152">Edytuj zmienne ciągów dla środowiska i preferencji.</span><span class="sxs-lookup"><span data-stu-id="08b2b-152">Edit the string variables for your environment and preferences.</span></span>  
  
 [!code-csharp[CryptoWalkThru#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#1)]
 [!code-vb[CryptoWalkThru#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#1)]  
  
## <a name="creating-an-asymmetric-key"></a><span data-ttu-id="08b2b-153">Tworzenie klucza asymetrycznego</span><span class="sxs-lookup"><span data-stu-id="08b2b-153">Creating an Asymmetric Key</span></span>  
 <span data-ttu-id="08b2b-154">To zadanie tworzy klucz asymetryczny, który szyfruje i odszyfrowuje <xref:System.Security.Cryptography.RijndaelManaged> klucz.</span><span class="sxs-lookup"><span data-stu-id="08b2b-154">This task creates an asymmetric key that encrypts and decrypts the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span> <span data-ttu-id="08b2b-155">Ten klucz został użyty do zaszyfrowania zawartości i wyświetla nazwę kontenera kluczy w kontrolce etykieta.</span><span class="sxs-lookup"><span data-stu-id="08b2b-155">This key was used to encrypt the content and it displays the key container name on the label control.</span></span>  
  
 <span data-ttu-id="08b2b-156">Dodaj następujący kod jako `Click` procedurę obsługi zdarzeń `Create Keys` dla przycisku (`buttonCreateAsmKeys_Click`).</span><span class="sxs-lookup"><span data-stu-id="08b2b-156">Add the following code as the `Click` event handler for the `Create Keys` button (`buttonCreateAsmKeys_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#2)]
 [!code-vb[CryptoWalkThru#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#2)]  
  
## <a name="encrypting-a-file"></a><span data-ttu-id="08b2b-157">Szyfrowanie pliku</span><span class="sxs-lookup"><span data-stu-id="08b2b-157">Encrypting a File</span></span>  
 <span data-ttu-id="08b2b-158">To zadanie obejmuje dwie metody: metoda obsługi zdarzeń dla `Encrypt File` przycisku (`buttonEncryptFile_Click`) i `EncryptFile` metody.</span><span class="sxs-lookup"><span data-stu-id="08b2b-158">This task involves two methods: the event handler method for the `Encrypt File` button (`buttonEncryptFile_Click`) and the `EncryptFile` method.</span></span> <span data-ttu-id="08b2b-159">Pierwsza metoda wyświetla okno dialogowe, w którym można wybrać plik i przekazuje nazwę pliku do drugiej metody, która wykonuje szyfrowanie.</span><span class="sxs-lookup"><span data-stu-id="08b2b-159">The first method displays a dialog box for selecting a file and passes the file name to the second method, which performs the encryption.</span></span>  
  
 <span data-ttu-id="08b2b-160">Zaszyfrowana zawartość, klucz i IV są zapisywane na jednym <xref:System.IO.FileStream>, który jest nazywany Pakietem szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="08b2b-160">The encrypted content, key, and IV are all saved to one <xref:System.IO.FileStream>, which is referred to as the encryption package.</span></span>  
  
 <span data-ttu-id="08b2b-161">`EncryptFile` Metoda wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="08b2b-161">The `EncryptFile` method does the following:</span></span>  
  
1. <span data-ttu-id="08b2b-162">Tworzy algorytm <xref:System.Security.Cryptography.RijndaelManaged> symetryczny do szyfrowania zawartości.</span><span class="sxs-lookup"><span data-stu-id="08b2b-162">Creates a <xref:System.Security.Cryptography.RijndaelManaged> symmetric algorithm to encrypt the content.</span></span>  
  
2. <span data-ttu-id="08b2b-163">Tworzy obiekt służący do <xref:System.Security.Cryptography.RijndaelManaged> szyfrowania klucza. <xref:System.Security.Cryptography.RSACryptoServiceProvider></span><span class="sxs-lookup"><span data-stu-id="08b2b-163">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to encrypt the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span>  
  
3. <span data-ttu-id="08b2b-164">Używa obiektu do odczytu i <xref:System.IO.FileStream> szyfrowania pliku źródłowego w blokach bajtów do obiektu docelowego <xref:System.IO.FileStream> dla zaszyfrowanego pliku. <xref:System.Security.Cryptography.CryptoStream></span><span class="sxs-lookup"><span data-stu-id="08b2b-164">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and encrypt the <xref:System.IO.FileStream> of the source file, in blocks of bytes, into a destination <xref:System.IO.FileStream> object for the encrypted file.</span></span>  
  
4. <span data-ttu-id="08b2b-165">Określa długość zaszyfrowanego klucza i IV i tworzy tablicę bajtową wartości ich długości.</span><span class="sxs-lookup"><span data-stu-id="08b2b-165">Determines the lengths of the encrypted key and IV, and creates byte arrays of their length values.</span></span>  
  
5. <span data-ttu-id="08b2b-166">Zapisuje wartości key, IV i ich długości do zaszyfrowanego pakietu.</span><span class="sxs-lookup"><span data-stu-id="08b2b-166">Writes the Key, IV, and their length values to the encrypted package.</span></span>  
  
 <span data-ttu-id="08b2b-167">Pakiet szyfrowania używa następującego formatu:</span><span class="sxs-lookup"><span data-stu-id="08b2b-167">The encryption package uses the following format:</span></span>  
  
- <span data-ttu-id="08b2b-168">Długość klucza, bajty 0-3</span><span class="sxs-lookup"><span data-stu-id="08b2b-168">Key length, bytes 0 - 3</span></span>  
  
- <span data-ttu-id="08b2b-169">Długość IV, bajtów 4-7</span><span class="sxs-lookup"><span data-stu-id="08b2b-169">IV length, bytes 4 - 7</span></span>  
  
- <span data-ttu-id="08b2b-170">Zaszyfrowany klucz</span><span class="sxs-lookup"><span data-stu-id="08b2b-170">Encrypted key</span></span>  
  
- <span data-ttu-id="08b2b-171">IV</span><span class="sxs-lookup"><span data-stu-id="08b2b-171">IV</span></span>  
  
- <span data-ttu-id="08b2b-172">Szyfrowanie tekstu</span><span class="sxs-lookup"><span data-stu-id="08b2b-172">Cipher text</span></span>  
  
 <span data-ttu-id="08b2b-173">Możesz użyć długości klucza i IV, aby określić punkty początkowe i długości wszystkich części pakietu szyfrującego, które mogą być następnie użyte do odszyfrowania pliku.</span><span class="sxs-lookup"><span data-stu-id="08b2b-173">You can use the lengths of the key and IV to determine the starting points and lengths of all parts of the encryption package, which can then be used to decrypt the file.</span></span>  
  
 <span data-ttu-id="08b2b-174">Dodaj następujący kod jako `Click` procedurę obsługi zdarzeń `Encrypt File` dla przycisku (`buttonEncryptFile_Click`).</span><span class="sxs-lookup"><span data-stu-id="08b2b-174">Add the following code as the `Click` event handler for the `Encrypt File` button (`buttonEncryptFile_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#3)]
 [!code-vb[CryptoWalkThru#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#3)]  
  
 <span data-ttu-id="08b2b-175">Dodaj następującą `EncryptFile` metodę do formularza.</span><span class="sxs-lookup"><span data-stu-id="08b2b-175">Add the following `EncryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#5)]
 [!code-vb[CryptoWalkThru#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#5)]  
  
## <a name="decrypting-a-file"></a><span data-ttu-id="08b2b-176">Odszyfrowywanie pliku</span><span class="sxs-lookup"><span data-stu-id="08b2b-176">Decrypting a File</span></span>  
 <span data-ttu-id="08b2b-177">To zadanie obejmuje dwie metody, metodę obsługi zdarzeń dla `Decrypt File` przycisku (`buttonDecryptFile_Click`) i `DecryptFile` metodę.</span><span class="sxs-lookup"><span data-stu-id="08b2b-177">This task involves two methods, the event handler method for the `Decrypt File` button (`buttonDecryptFile_Click`), and the `DecryptFile` method.</span></span> <span data-ttu-id="08b2b-178">Pierwsza metoda wyświetla okno dialogowe, w którym można wybrać plik i przekazuje jego nazwę pliku do drugiej metody, która wykonuje odszyfrowywanie.</span><span class="sxs-lookup"><span data-stu-id="08b2b-178">The first method displays a dialog box for selecting a file and passes its file name to the second method, which performs the decryption.</span></span>  
  
 <span data-ttu-id="08b2b-179">`Decrypt` Metoda wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="08b2b-179">The `Decrypt` method does the following:</span></span>  
  
1. <span data-ttu-id="08b2b-180">Tworzy algorytm <xref:System.Security.Cryptography.RijndaelManaged> symetryczny służący do odszyfrowywania zawartości.</span><span class="sxs-lookup"><span data-stu-id="08b2b-180">Creates a <xref:System.Security.Cryptography.RijndaelManaged> symmetric algorithm to decrypt the content.</span></span>  
  
2. <span data-ttu-id="08b2b-181">Odczytuje pierwsze osiem bajtów <xref:System.IO.FileStream> zaszyfrowanego pakietu do tablic bajtów w celu uzyskania długości zaszyfrowanego klucza i IV.</span><span class="sxs-lookup"><span data-stu-id="08b2b-181">Reads the first eight bytes of the <xref:System.IO.FileStream> of the encrypted package into byte arrays to obtain the lengths of the encrypted key and the IV.</span></span>  
  
3. <span data-ttu-id="08b2b-182">Wyodrębnia klucz i IV z pakietu szyfrowania do tablic bajtowych.</span><span class="sxs-lookup"><span data-stu-id="08b2b-182">Extracts the key and IV from the encryption package into byte arrays.</span></span>  
  
4. <span data-ttu-id="08b2b-183">Tworzy obiekt do odszyfrowania <xref:System.Security.Cryptography.RijndaelManaged>klucza. <xref:System.Security.Cryptography.RSACryptoServiceProvider></span><span class="sxs-lookup"><span data-stu-id="08b2b-183">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to decrypt the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span>  
  
5. <span data-ttu-id="08b2b-184">Używa obiektu do odczytywania i odszyfrowywania sekcji <xref:System.IO.FileStream> szyfrowania tekstu pakietu szyfrowania w blokach bajtów do <xref:System.IO.FileStream> obiektu w odszyfrowanym pliku. <xref:System.Security.Cryptography.CryptoStream></span><span class="sxs-lookup"><span data-stu-id="08b2b-184">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and decrypt the cipher text section of the <xref:System.IO.FileStream> encryption package, in blocks of bytes, into the <xref:System.IO.FileStream> object for the decrypted file.</span></span> <span data-ttu-id="08b2b-185">Po zakończeniu odszyfrowywania zostanie zakończone.</span><span class="sxs-lookup"><span data-stu-id="08b2b-185">When this is finished, the decryption is completed.</span></span>  
  
 <span data-ttu-id="08b2b-186">Dodaj następujący kod jako `Click` procedurę obsługi zdarzeń `Decrypt File` dla przycisku.</span><span class="sxs-lookup"><span data-stu-id="08b2b-186">Add the following code as the `Click` event handler for the `Decrypt File` button.</span></span>  
  
 [!code-csharp[CryptoWalkThru#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#4)]
 [!code-vb[CryptoWalkThru#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#4)]  
  
 <span data-ttu-id="08b2b-187">Dodaj następującą `DecryptFile` metodę do formularza.</span><span class="sxs-lookup"><span data-stu-id="08b2b-187">Add the following `DecryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#6)]
 [!code-vb[CryptoWalkThru#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#6)]  
  
## <a name="exporting-a-public-key"></a><span data-ttu-id="08b2b-188">Eksportowanie klucza publicznego</span><span class="sxs-lookup"><span data-stu-id="08b2b-188">Exporting a Public Key</span></span>  
 <span data-ttu-id="08b2b-189">To zadanie służy do zapisywania klucza utworzonego przez `Create Keys` przycisk do pliku.</span><span class="sxs-lookup"><span data-stu-id="08b2b-189">This task saves the key created by the `Create Keys` button to a file.</span></span> <span data-ttu-id="08b2b-190">Eksportuje tylko parametry publiczne.</span><span class="sxs-lookup"><span data-stu-id="08b2b-190">It exports only the public parameters.</span></span>  
  
 <span data-ttu-id="08b2b-191">To zadanie symuluje scenariusz dla Alicja przekazującej Roberta swój klucz publiczny, aby mógł szyfrować pliki.</span><span class="sxs-lookup"><span data-stu-id="08b2b-191">This task simulates the scenario of Alice giving Bob her public key so that he can encrypt files for her.</span></span> <span data-ttu-id="08b2b-192">Osoby, które mają ten klucz publiczny, nie będą w stanie odszyfrować, ponieważ nie mają pełnej pary kluczy z parametrami prywatnymi.</span><span class="sxs-lookup"><span data-stu-id="08b2b-192">He and others who have that public key will not be able to decrypt them because they do not have the full key pair with private parameters.</span></span>  
  
 <span data-ttu-id="08b2b-193">Dodaj następujący kod jako `Click` procedurę obsługi zdarzeń `Export Public Key` dla przycisku (`buttonExportPublicKey_Click`).</span><span class="sxs-lookup"><span data-stu-id="08b2b-193">Add the following code as the `Click` event handler for the `Export Public Key` button (`buttonExportPublicKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#8)]
 [!code-vb[CryptoWalkThru#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#8)]  
  
## <a name="importing-a-public-key"></a><span data-ttu-id="08b2b-194">Importowanie klucza publicznego</span><span class="sxs-lookup"><span data-stu-id="08b2b-194">Importing a Public Key</span></span>  
 <span data-ttu-id="08b2b-195">To zadanie ładuje klucz z tylko parametrami publicznymi, utworzonym przez `Export Public Key` przycisk i ustawia go jako nazwę kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="08b2b-195">This task loads the key with only public parameters, as created by the `Export Public Key` button, and sets it as the key container name.</span></span>  
  
 <span data-ttu-id="08b2b-196">To zadanie symuluje scenariusz ładowania klucza Alicja z tylko parametrami publicznymi, dzięki czemu może zaszyfrować pliki.</span><span class="sxs-lookup"><span data-stu-id="08b2b-196">This task simulates the scenario of Bob loading Alice's key with only public parameters so he can encrypt files for her.</span></span>  
  
 <span data-ttu-id="08b2b-197">Dodaj następujący kod jako `Click` procedurę obsługi zdarzeń `Import Public Key` dla przycisku (`buttonImportPublicKey_Click`).</span><span class="sxs-lookup"><span data-stu-id="08b2b-197">Add the following code as the `Click` event handler for the `Import Public Key` button (`buttonImportPublicKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#9)]
 [!code-vb[CryptoWalkThru#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#9)]  
  
## <a name="getting-a-private-key"></a><span data-ttu-id="08b2b-198">Pobieranie klucza prywatnego</span><span class="sxs-lookup"><span data-stu-id="08b2b-198">Getting a Private Key</span></span>  
 <span data-ttu-id="08b2b-199">To zadanie ustawia nazwę kontenera kluczy na nazwę klucza utworzonego za pomocą `Create Keys` przycisku.</span><span class="sxs-lookup"><span data-stu-id="08b2b-199">This task sets the key container name to the name of the key created by using the `Create Keys` button.</span></span> <span data-ttu-id="08b2b-200">Kontener kluczy będzie zawierać pełną parę kluczy z parametrami prywatnymi.</span><span class="sxs-lookup"><span data-stu-id="08b2b-200">The key container will contain the full key pair with private parameters.</span></span>  
  
 <span data-ttu-id="08b2b-201">To zadanie symuluje scenariusz Alicja przy użyciu klucza prywatnego w celu odszyfrowania plików zaszyfrowanych przez Robert.</span><span class="sxs-lookup"><span data-stu-id="08b2b-201">This task simulates the scenario of Alice using her private key to decrypt files encrypted by Bob.</span></span>  
  
 <span data-ttu-id="08b2b-202">Dodaj następujący kod jako `Click` procedurę obsługi zdarzeń `Get Private Key` dla przycisku (`buttonGetPrivateKey_Click`).</span><span class="sxs-lookup"><span data-stu-id="08b2b-202">Add the following code as the `Click` event handler for the `Get Private Key` button (`buttonGetPrivateKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#7)]
 [!code-vb[CryptoWalkThru#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#7)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="08b2b-203">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="08b2b-203">Testing the Application</span></span>  
 <span data-ttu-id="08b2b-204">Po skompilowaniu aplikacji wykonaj następujące scenariusze testowania.</span><span class="sxs-lookup"><span data-stu-id="08b2b-204">After you have built the application, perform the following testing scenarios.</span></span>  
  
#### <a name="to-create-keys-encrypt-and-decrypt"></a><span data-ttu-id="08b2b-205">Aby utworzyć klucze, szyfrowanie i odszyfrowywanie</span><span class="sxs-lookup"><span data-stu-id="08b2b-205">To create keys, encrypt, and decrypt</span></span>  
  
1. <span data-ttu-id="08b2b-206">`Create Keys` Kliknij przycisk.</span><span class="sxs-lookup"><span data-stu-id="08b2b-206">Click the `Create Keys` button.</span></span> <span data-ttu-id="08b2b-207">Etykieta Wyświetla nazwę klucza i pokazuje, że jest to pełna para kluczy.</span><span class="sxs-lookup"><span data-stu-id="08b2b-207">The label displays the key name and shows that it is a full key pair.</span></span>  
  
2. <span data-ttu-id="08b2b-208">`Export Public Key` Kliknij przycisk.</span><span class="sxs-lookup"><span data-stu-id="08b2b-208">Click the `Export Public Key` button.</span></span> <span data-ttu-id="08b2b-209">Należy zauważyć, że eksportowanie parametrów klucza publicznego nie zmienia bieżącego klucza.</span><span class="sxs-lookup"><span data-stu-id="08b2b-209">Note that exporting the public key parameters does not change the current key.</span></span>  
  
3. <span data-ttu-id="08b2b-210">`Encrypt File` Kliknij przycisk i wybierz plik.</span><span class="sxs-lookup"><span data-stu-id="08b2b-210">Click the `Encrypt File` button and select a file.</span></span>  
  
4. <span data-ttu-id="08b2b-211">`Decrypt File` Kliknij przycisk i wybierz plik, który został zaszyfrowany.</span><span class="sxs-lookup"><span data-stu-id="08b2b-211">Click the `Decrypt File` button and select the file just encrypted.</span></span>  
  
5. <span data-ttu-id="08b2b-212">Zapoznaj się z odszyfrowaniem pliku.</span><span class="sxs-lookup"><span data-stu-id="08b2b-212">Examine the file just decrypted.</span></span>  
  
6. <span data-ttu-id="08b2b-213">Zamknij aplikację i uruchom ją ponownie, aby przetestować pobieranie utrwalonych kontenerów kluczy w następnym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="08b2b-213">Close the application and restart it to test retrieving persisted key containers in the next scenario.</span></span>  
  
#### <a name="to-encrypt-using-the-public-key"></a><span data-ttu-id="08b2b-214">Aby zaszyfrować przy użyciu klucza publicznego</span><span class="sxs-lookup"><span data-stu-id="08b2b-214">To encrypt using the public key</span></span>  
  
1. <span data-ttu-id="08b2b-215">`Import Public Key` Kliknij przycisk.</span><span class="sxs-lookup"><span data-stu-id="08b2b-215">Click the `Import Public Key` button.</span></span> <span data-ttu-id="08b2b-216">Etykieta Wyświetla nazwę klucza i pokazuje, że jest tylko publiczna.</span><span class="sxs-lookup"><span data-stu-id="08b2b-216">The label displays the key name and shows that it is public only.</span></span>  
  
2. <span data-ttu-id="08b2b-217">`Encrypt File` Kliknij przycisk i wybierz plik.</span><span class="sxs-lookup"><span data-stu-id="08b2b-217">Click the `Encrypt File` button and select a file.</span></span>  
  
3. <span data-ttu-id="08b2b-218">`Decrypt File` Kliknij przycisk i wybierz plik, który został zaszyfrowany.</span><span class="sxs-lookup"><span data-stu-id="08b2b-218">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="08b2b-219">Nie powiedzie się, ponieważ musisz mieć klucz prywatny do odszyfrowania.</span><span class="sxs-lookup"><span data-stu-id="08b2b-219">This will fail because you must have the private key to decrypt.</span></span>  
  
 <span data-ttu-id="08b2b-220">W tym scenariuszu przedstawiono tylko klucz publiczny do szyfrowania pliku dla innej osoby.</span><span class="sxs-lookup"><span data-stu-id="08b2b-220">This scenario demonstrates having only the public key to encrypt a file for another person.</span></span> <span data-ttu-id="08b2b-221">Zwykle osoba ta może uzyskać tylko klucz publiczny i wstrzymać klucz prywatny do odszyfrowania.</span><span class="sxs-lookup"><span data-stu-id="08b2b-221">Typically that person would give you only the public key and withhold the private key for decryption.</span></span>  
  
#### <a name="to-decrypt-using-the-private-key"></a><span data-ttu-id="08b2b-222">Aby odszyfrować przy użyciu klucza prywatnego</span><span class="sxs-lookup"><span data-stu-id="08b2b-222">To decrypt using the private key</span></span>  
  
1. <span data-ttu-id="08b2b-223">`Get Private Key` Kliknij przycisk.</span><span class="sxs-lookup"><span data-stu-id="08b2b-223">Click the `Get Private Key` button.</span></span> <span data-ttu-id="08b2b-224">Etykieta Wyświetla nazwę klucza i pokazuje, czy jest to pełna para kluczy.</span><span class="sxs-lookup"><span data-stu-id="08b2b-224">The label displays the key name and shows whether it is the full key pair.</span></span>  
  
2. <span data-ttu-id="08b2b-225">`Decrypt File` Kliknij przycisk i wybierz plik, który został zaszyfrowany.</span><span class="sxs-lookup"><span data-stu-id="08b2b-225">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="08b2b-226">Ta operacja zakończy się pomyślnie, ponieważ masz pełną parę kluczy do odszyfrowania.</span><span class="sxs-lookup"><span data-stu-id="08b2b-226">This will be successful because you have the full key pair to decrypt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08b2b-227">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="08b2b-227">See also</span></span>

- [<span data-ttu-id="08b2b-228">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="08b2b-228">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
