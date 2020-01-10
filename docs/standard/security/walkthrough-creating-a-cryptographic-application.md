---
title: 'Wskazówki: tworzenie aplikacji kryptograficznej'
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
ms.openlocfilehash: 6e2d9b8bebdfd2ea5d5507cc73d444fa8bf785fb
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705837"
---
# <a name="walkthrough-creating-a-cryptographic-application"></a><span data-ttu-id="29bd0-102">Wskazówki: tworzenie aplikacji kryptograficznej</span><span class="sxs-lookup"><span data-stu-id="29bd0-102">Walkthrough: Creating a Cryptographic Application</span></span>
<span data-ttu-id="29bd0-103">W tym instruktażu pokazano, jak szyfrować i odszyfrowywać zawartość.</span><span class="sxs-lookup"><span data-stu-id="29bd0-103">This walkthrough demonstrates how to encrypt and decrypt content.</span></span> <span data-ttu-id="29bd0-104">Przykłady kodu są przeznaczone dla aplikacji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="29bd0-104">The code examples are designed for a Windows Forms application.</span></span> <span data-ttu-id="29bd0-105">Ta aplikacja nie pokazuje rzeczywistych scenariuszy, takich jak korzystanie z kart inteligentnych.</span><span class="sxs-lookup"><span data-stu-id="29bd0-105">This application does not demonstrate real world scenarios, such as using smart cards.</span></span> <span data-ttu-id="29bd0-106">Zamiast tego pokazuje podstawowe informacje dotyczące szyfrowania i odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="29bd0-106">Instead, it demonstrates the fundamentals of encryption and decryption.</span></span>  
  
 <span data-ttu-id="29bd0-107">W tym instruktażu zastosowano następujące wytyczne dotyczące szyfrowania:</span><span class="sxs-lookup"><span data-stu-id="29bd0-107">This walkthrough uses the following guidelines for encryption:</span></span>  
  
- <span data-ttu-id="29bd0-108">Użyj klasy <xref:System.Security.Cryptography.RijndaelManaged>, algorytmu symetrycznego, aby szyfrować i odszyfrowywać dane przy użyciu automatycznie generowanych <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> i <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>.</span><span class="sxs-lookup"><span data-stu-id="29bd0-108">Use the <xref:System.Security.Cryptography.RijndaelManaged> class, a symmetric algorithm, to encrypt and decrypt data by using its automatically generated <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> and <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>.</span></span>  
  
- <span data-ttu-id="29bd0-109">Użyj <xref:System.Security.Cryptography.RSACryptoServiceProvider>, algorytmu asymetrycznego, aby szyfrować i odszyfrowywać klucz do danych szyfrowanych przez <xref:System.Security.Cryptography.RijndaelManaged>.</span><span class="sxs-lookup"><span data-stu-id="29bd0-109">Use the <xref:System.Security.Cryptography.RSACryptoServiceProvider>, an asymmetric algorithm, to encrypt and decrypt the key to the data encrypted by <xref:System.Security.Cryptography.RijndaelManaged>.</span></span> <span data-ttu-id="29bd0-110">Algorytmy asymetryczne najlepiej używać w przypadku mniejszych ilości danych, takich jak klucz.</span><span class="sxs-lookup"><span data-stu-id="29bd0-110">Asymmetric algorithms are best used for smaller amounts of data, such as a key.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="29bd0-111">Jeśli chcesz chronić dane na komputerze zamiast wymieniać zaszyfrowaną zawartość z innymi osobami, rozważ użycie klas <xref:System.Security.Cryptography.ProtectedData> lub <xref:System.Security.Cryptography.ProtectedMemory>.</span><span class="sxs-lookup"><span data-stu-id="29bd0-111">If you want to protect data on your computer instead of exchanging encrypted content with other people, consider using the <xref:System.Security.Cryptography.ProtectedData> or <xref:System.Security.Cryptography.ProtectedMemory> classes.</span></span>  
  
 <span data-ttu-id="29bd0-112">Poniższa tabela zawiera podsumowanie zadań kryptograficznych w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="29bd0-112">The following table summarizes the cryptographic tasks in this topic.</span></span>  
  
|<span data-ttu-id="29bd0-113">Zadanie</span><span class="sxs-lookup"><span data-stu-id="29bd0-113">Task</span></span>|<span data-ttu-id="29bd0-114">Opis</span><span class="sxs-lookup"><span data-stu-id="29bd0-114">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="29bd0-115">Tworzenie aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="29bd0-115">Creating a Windows Forms application</span></span>|<span data-ttu-id="29bd0-116">Wyświetla listę kontrolek, które są wymagane do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="29bd0-116">Lists the controls that are required to run the application.</span></span>|  
|<span data-ttu-id="29bd0-117">Deklarowanie obiektów globalnych</span><span class="sxs-lookup"><span data-stu-id="29bd0-117">Declaring global objects</span></span>|<span data-ttu-id="29bd0-118">Deklaruje zmienne ścieżki ciągów, <xref:System.Security.Cryptography.CspParameters>i <xref:System.Security.Cryptography.RSACryptoServiceProvider> do posiadania globalnego kontekstu klasy <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="29bd0-118">Declares string path variables, the <xref:System.Security.Cryptography.CspParameters>, and the <xref:System.Security.Cryptography.RSACryptoServiceProvider> to have global context of the <xref:System.Windows.Forms.Form> class.</span></span>|  
|<span data-ttu-id="29bd0-119">Tworzenie klucza asymetrycznego</span><span class="sxs-lookup"><span data-stu-id="29bd0-119">Creating an asymmetric key</span></span>|<span data-ttu-id="29bd0-120">Tworzy asymetryczną parę wartości klucza publicznego i prywatnego i przypisuje mu nazwę kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="29bd0-120">Creates an asymmetric public and private key value pair and assigns it a key container name.</span></span>|  
|<span data-ttu-id="29bd0-121">Szyfrowanie pliku</span><span class="sxs-lookup"><span data-stu-id="29bd0-121">Encrypting a file</span></span>|<span data-ttu-id="29bd0-122">Wyświetla okno dialogowe, w którym można wybrać plik do szyfrowania i szyfruje plik.</span><span class="sxs-lookup"><span data-stu-id="29bd0-122">Displays a dialog box to select a file for encryption and encrypts the file.</span></span>|  
|<span data-ttu-id="29bd0-123">Odszyfrowywanie pliku</span><span class="sxs-lookup"><span data-stu-id="29bd0-123">Decrypting a file</span></span>|<span data-ttu-id="29bd0-124">Wyświetla okno dialogowe, w którym można wybrać zaszyfrowany plik do odszyfrowania i odszyfrować plik.</span><span class="sxs-lookup"><span data-stu-id="29bd0-124">Displays a dialog box to select an encrypted file for decryption and decrypts the file.</span></span>|  
|<span data-ttu-id="29bd0-125">Pobieranie klucza prywatnego</span><span class="sxs-lookup"><span data-stu-id="29bd0-125">Getting a private key</span></span>|<span data-ttu-id="29bd0-126">Pobiera pełną parę kluczy przy użyciu nazwy kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="29bd0-126">Gets the full key pair using the key container name.</span></span>|  
|<span data-ttu-id="29bd0-127">Eksportowanie klucza publicznego</span><span class="sxs-lookup"><span data-stu-id="29bd0-127">Exporting a public key</span></span>|<span data-ttu-id="29bd0-128">Zapisuje klucz do pliku XML tylko z parametrami publicznymi.</span><span class="sxs-lookup"><span data-stu-id="29bd0-128">Saves the key to an XML file with only public parameters.</span></span>|  
|<span data-ttu-id="29bd0-129">Importowanie klucza publicznego</span><span class="sxs-lookup"><span data-stu-id="29bd0-129">Importing a public key</span></span>|<span data-ttu-id="29bd0-130">Ładuje klucz z pliku XML do kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="29bd0-130">Loads the key from an XML file into the key container.</span></span>|  
|<span data-ttu-id="29bd0-131">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="29bd0-131">Testing the application</span></span>|<span data-ttu-id="29bd0-132">Wyświetla listę procedur testowania tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="29bd0-132">Lists procedures for testing this application.</span></span>|  
  
## <a name="prerequisites"></a><span data-ttu-id="29bd0-133">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="29bd0-133">Prerequisites</span></span>  
 <span data-ttu-id="29bd0-134">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="29bd0-134">You need the following components to complete this walkthrough:</span></span>  
  
- <span data-ttu-id="29bd0-135">Odwołania do przestrzeni nazw <xref:System.IO> i <xref:System.Security.Cryptography>.</span><span class="sxs-lookup"><span data-stu-id="29bd0-135">References to the <xref:System.IO> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
## <a name="creating-a-windows-forms-application"></a><span data-ttu-id="29bd0-136">Tworzenie aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="29bd0-136">Creating a Windows Forms Application</span></span>  
 <span data-ttu-id="29bd0-137">Większość przykładów kodu w tym instruktażu została zaprojektowana jako programy obsługi zdarzeń dla kontrolek Button.</span><span class="sxs-lookup"><span data-stu-id="29bd0-137">Most of the code examples in this walkthrough are designed to be event handlers for button controls.</span></span> <span data-ttu-id="29bd0-138">Poniższa tabela zawiera listę formantów wymaganych dla przykładowej aplikacji i ich wymaganych nazw w celu dopasowania do przykładów kodu.</span><span class="sxs-lookup"><span data-stu-id="29bd0-138">The following table lists the controls required for the sample application and their required names to match the code examples.</span></span>  
  
|<span data-ttu-id="29bd0-139">Kontrolka</span><span class="sxs-lookup"><span data-stu-id="29bd0-139">Control</span></span>|<span data-ttu-id="29bd0-140">Nazwa</span><span class="sxs-lookup"><span data-stu-id="29bd0-140">Name</span></span>|<span data-ttu-id="29bd0-141">Właściwość Text (zgodnie z wymaganiami)</span><span class="sxs-lookup"><span data-stu-id="29bd0-141">Text property (as needed)</span></span>|  
|-------------|----------|---------------------------------|  
|<xref:System.Windows.Forms.Button>|`buttonEncryptFile`|<span data-ttu-id="29bd0-142">Szyfruj plik</span><span class="sxs-lookup"><span data-stu-id="29bd0-142">Encrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonDecryptFile`|<span data-ttu-id="29bd0-143">Odszyfruj plik</span><span class="sxs-lookup"><span data-stu-id="29bd0-143">Decrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonCreateAsmKeys`|<span data-ttu-id="29bd0-144">Utwórz klucze</span><span class="sxs-lookup"><span data-stu-id="29bd0-144">Create Keys</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonExportPublicKey`|<span data-ttu-id="29bd0-145">Eksportuj klucz publiczny</span><span class="sxs-lookup"><span data-stu-id="29bd0-145">Export Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonImportPublicKey`|<span data-ttu-id="29bd0-146">Importuj klucz publiczny</span><span class="sxs-lookup"><span data-stu-id="29bd0-146">Import Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonGetPrivateKey`|<span data-ttu-id="29bd0-147">Pobierz klucz prywatny</span><span class="sxs-lookup"><span data-stu-id="29bd0-147">Get Private Key</span></span>|  
|<xref:System.Windows.Forms.Label>|`label1`|<span data-ttu-id="29bd0-148">Nie ustawiono klucza</span><span class="sxs-lookup"><span data-stu-id="29bd0-148">Key not set</span></span>|  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog2`||  
  
 <span data-ttu-id="29bd0-149">Kliknij dwukrotnie przyciski w projektancie programu Visual Studio, aby utworzyć obsługę zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="29bd0-149">Double-click the buttons in the  Visual Studio designer to create their event handlers.</span></span>  
  
## <a name="declaring-global-objects"></a><span data-ttu-id="29bd0-150">Deklarowanie obiektów globalnych</span><span class="sxs-lookup"><span data-stu-id="29bd0-150">Declaring Global Objects</span></span>  
 <span data-ttu-id="29bd0-151">Dodaj następujący kod do konstruktora formularza.</span><span class="sxs-lookup"><span data-stu-id="29bd0-151">Add the following code to the Form's constructor.</span></span> <span data-ttu-id="29bd0-152">Edytuj zmienne ciągów dla środowiska i preferencji.</span><span class="sxs-lookup"><span data-stu-id="29bd0-152">Edit the string variables for your environment and preferences.</span></span>  
  
 [!code-csharp[CryptoWalkThru#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#1)]
 [!code-vb[CryptoWalkThru#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#1)]  
  
## <a name="creating-an-asymmetric-key"></a><span data-ttu-id="29bd0-153">Tworzenie klucza asymetrycznego</span><span class="sxs-lookup"><span data-stu-id="29bd0-153">Creating an Asymmetric Key</span></span>  
 <span data-ttu-id="29bd0-154">To zadanie tworzy klucz asymetryczny, który szyfruje i odszyfrowuje klucz <xref:System.Security.Cryptography.RijndaelManaged>.</span><span class="sxs-lookup"><span data-stu-id="29bd0-154">This task creates an asymmetric key that encrypts and decrypts the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span> <span data-ttu-id="29bd0-155">Ten klucz został użyty do zaszyfrowania zawartości i wyświetla nazwę kontenera kluczy w kontrolce etykieta.</span><span class="sxs-lookup"><span data-stu-id="29bd0-155">This key was used to encrypt the content and it displays the key container name on the label control.</span></span>  
  
 <span data-ttu-id="29bd0-156">Dodaj następujący kod jako procedurę obsługi zdarzeń `Click` dla przycisku `Create Keys` (`buttonCreateAsmKeys_Click`).</span><span class="sxs-lookup"><span data-stu-id="29bd0-156">Add the following code as the `Click` event handler for the `Create Keys` button (`buttonCreateAsmKeys_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#2)]
 [!code-vb[CryptoWalkThru#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#2)]  
  
## <a name="encrypting-a-file"></a><span data-ttu-id="29bd0-157">Szyfrowanie pliku</span><span class="sxs-lookup"><span data-stu-id="29bd0-157">Encrypting a File</span></span>  
 <span data-ttu-id="29bd0-158">To zadanie obejmuje dwie metody: metoda obsługi zdarzeń dla przycisku `Encrypt File` (`buttonEncryptFile_Click`) i metody `EncryptFile`.</span><span class="sxs-lookup"><span data-stu-id="29bd0-158">This task involves two methods: the event handler method for the `Encrypt File` button (`buttonEncryptFile_Click`) and the `EncryptFile` method.</span></span> <span data-ttu-id="29bd0-159">Pierwsza metoda wyświetla okno dialogowe, w którym można wybrać plik i przekazuje nazwę pliku do drugiej metody, która wykonuje szyfrowanie.</span><span class="sxs-lookup"><span data-stu-id="29bd0-159">The first method displays a dialog box for selecting a file and passes the file name to the second method, which performs the encryption.</span></span>  
  
 <span data-ttu-id="29bd0-160">Zaszyfrowana zawartość, klucz i IV są zapisywane w jednym <xref:System.IO.FileStream>, który jest nazywany Pakietem szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="29bd0-160">The encrypted content, key, and IV are all saved to one <xref:System.IO.FileStream>, which is referred to as the encryption package.</span></span>  
  
 <span data-ttu-id="29bd0-161">Metoda `EncryptFile` wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="29bd0-161">The `EncryptFile` method does the following:</span></span>  
  
1. <span data-ttu-id="29bd0-162">Tworzy algorytm symetryczny <xref:System.Security.Cryptography.RijndaelManaged> w celu zaszyfrowania zawartości.</span><span class="sxs-lookup"><span data-stu-id="29bd0-162">Creates a <xref:System.Security.Cryptography.RijndaelManaged> symmetric algorithm to encrypt the content.</span></span>  
  
2. <span data-ttu-id="29bd0-163">Tworzy obiekt <xref:System.Security.Cryptography.RSACryptoServiceProvider>, aby zaszyfrować klucz <xref:System.Security.Cryptography.RijndaelManaged>.</span><span class="sxs-lookup"><span data-stu-id="29bd0-163">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to encrypt the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span>  
  
3. <span data-ttu-id="29bd0-164">Używa obiektu <xref:System.Security.Cryptography.CryptoStream> do odczytywania i szyfrowania <xref:System.IO.FileStream> pliku źródłowego w blokach bajtów do docelowego obiektu <xref:System.IO.FileStream> dla zaszyfrowanego pliku.</span><span class="sxs-lookup"><span data-stu-id="29bd0-164">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and encrypt the <xref:System.IO.FileStream> of the source file, in blocks of bytes, into a destination <xref:System.IO.FileStream> object for the encrypted file.</span></span>  
  
4. <span data-ttu-id="29bd0-165">Określa długość zaszyfrowanego klucza i IV i tworzy tablicę bajtową wartości ich długości.</span><span class="sxs-lookup"><span data-stu-id="29bd0-165">Determines the lengths of the encrypted key and IV, and creates byte arrays of their length values.</span></span>  
  
5. <span data-ttu-id="29bd0-166">Zapisuje wartości key, IV i ich długości do zaszyfrowanego pakietu.</span><span class="sxs-lookup"><span data-stu-id="29bd0-166">Writes the Key, IV, and their length values to the encrypted package.</span></span>  
  
 <span data-ttu-id="29bd0-167">Pakiet szyfrowania używa następującego formatu:</span><span class="sxs-lookup"><span data-stu-id="29bd0-167">The encryption package uses the following format:</span></span>  
  
- <span data-ttu-id="29bd0-168">Długość klucza, bajty 0-3</span><span class="sxs-lookup"><span data-stu-id="29bd0-168">Key length, bytes 0 - 3</span></span>  
  
- <span data-ttu-id="29bd0-169">Długość IV, bajtów 4-7</span><span class="sxs-lookup"><span data-stu-id="29bd0-169">IV length, bytes 4 - 7</span></span>  
  
- <span data-ttu-id="29bd0-170">Zaszyfrowany klucz</span><span class="sxs-lookup"><span data-stu-id="29bd0-170">Encrypted key</span></span>  
  
- <span data-ttu-id="29bd0-171">IV</span><span class="sxs-lookup"><span data-stu-id="29bd0-171">IV</span></span>  
  
- <span data-ttu-id="29bd0-172">Szyfrowanie tekstu</span><span class="sxs-lookup"><span data-stu-id="29bd0-172">Cipher text</span></span>  
  
 <span data-ttu-id="29bd0-173">Możesz użyć długości klucza i IV, aby określić punkty początkowe i długości wszystkich części pakietu szyfrującego, które mogą być następnie użyte do odszyfrowania pliku.</span><span class="sxs-lookup"><span data-stu-id="29bd0-173">You can use the lengths of the key and IV to determine the starting points and lengths of all parts of the encryption package, which can then be used to decrypt the file.</span></span>  
  
 <span data-ttu-id="29bd0-174">Dodaj następujący kod jako procedurę obsługi zdarzeń `Click` dla przycisku `Encrypt File` (`buttonEncryptFile_Click`).</span><span class="sxs-lookup"><span data-stu-id="29bd0-174">Add the following code as the `Click` event handler for the `Encrypt File` button (`buttonEncryptFile_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#3)]
 [!code-vb[CryptoWalkThru#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#3)]  
  
 <span data-ttu-id="29bd0-175">Dodaj następującą metodę `EncryptFile` do formularza.</span><span class="sxs-lookup"><span data-stu-id="29bd0-175">Add the following `EncryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#5)]
 [!code-vb[CryptoWalkThru#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#5)]  
  
## <a name="decrypting-a-file"></a><span data-ttu-id="29bd0-176">Odszyfrowywanie pliku</span><span class="sxs-lookup"><span data-stu-id="29bd0-176">Decrypting a File</span></span>  
 <span data-ttu-id="29bd0-177">To zadanie obejmuje dwie metody, metodę obsługi zdarzeń dla przycisku `Decrypt File` (`buttonDecryptFile_Click`) i metodę `DecryptFile`.</span><span class="sxs-lookup"><span data-stu-id="29bd0-177">This task involves two methods, the event handler method for the `Decrypt File` button (`buttonDecryptFile_Click`), and the `DecryptFile` method.</span></span> <span data-ttu-id="29bd0-178">Pierwsza metoda wyświetla okno dialogowe, w którym można wybrać plik i przekazuje jego nazwę pliku do drugiej metody, która wykonuje odszyfrowywanie.</span><span class="sxs-lookup"><span data-stu-id="29bd0-178">The first method displays a dialog box for selecting a file and passes its file name to the second method, which performs the decryption.</span></span>  
  
 <span data-ttu-id="29bd0-179">Metoda `Decrypt` wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="29bd0-179">The `Decrypt` method does the following:</span></span>  
  
1. <span data-ttu-id="29bd0-180">Tworzy algorytm symetryczne <xref:System.Security.Cryptography.RijndaelManaged> w celu odszyfrowania zawartości.</span><span class="sxs-lookup"><span data-stu-id="29bd0-180">Creates a <xref:System.Security.Cryptography.RijndaelManaged> symmetric algorithm to decrypt the content.</span></span>  
  
2. <span data-ttu-id="29bd0-181">Odczytuje pierwsze osiem bajtów <xref:System.IO.FileStream> zaszyfrowanego pakietu do tablic bajtowych w celu uzyskania długości zaszyfrowanego klucza i IV.</span><span class="sxs-lookup"><span data-stu-id="29bd0-181">Reads the first eight bytes of the <xref:System.IO.FileStream> of the encrypted package into byte arrays to obtain the lengths of the encrypted key and the IV.</span></span>  
  
3. <span data-ttu-id="29bd0-182">Wyodrębnia klucz i IV z pakietu szyfrowania do tablic bajtowych.</span><span class="sxs-lookup"><span data-stu-id="29bd0-182">Extracts the key and IV from the encryption package into byte arrays.</span></span>  
  
4. <span data-ttu-id="29bd0-183">Tworzy obiekt <xref:System.Security.Cryptography.RSACryptoServiceProvider> do odszyfrowania klucza <xref:System.Security.Cryptography.RijndaelManaged>.</span><span class="sxs-lookup"><span data-stu-id="29bd0-183">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to decrypt the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span>  
  
5. <span data-ttu-id="29bd0-184">Używa obiektu <xref:System.Security.Cryptography.CryptoStream> do odczytywania i odszyfrowywania sekcji szyfrowania tekstu pakietu <xref:System.IO.FileStream> Encryption w blokach bajtów do obiektu <xref:System.IO.FileStream> odszyfrowywanego pliku.</span><span class="sxs-lookup"><span data-stu-id="29bd0-184">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and decrypt the cipher text section of the <xref:System.IO.FileStream> encryption package, in blocks of bytes, into the <xref:System.IO.FileStream> object for the decrypted file.</span></span> <span data-ttu-id="29bd0-185">Po zakończeniu odszyfrowywania zostanie zakończone.</span><span class="sxs-lookup"><span data-stu-id="29bd0-185">When this is finished, the decryption is completed.</span></span>  
  
 <span data-ttu-id="29bd0-186">Dodaj następujący kod jako procedurę obsługi zdarzeń `Click` dla przycisku `Decrypt File`.</span><span class="sxs-lookup"><span data-stu-id="29bd0-186">Add the following code as the `Click` event handler for the `Decrypt File` button.</span></span>  
  
 [!code-csharp[CryptoWalkThru#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#4)]
 [!code-vb[CryptoWalkThru#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#4)]  
  
 <span data-ttu-id="29bd0-187">Dodaj następującą metodę `DecryptFile` do formularza.</span><span class="sxs-lookup"><span data-stu-id="29bd0-187">Add the following `DecryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#6)]
 [!code-vb[CryptoWalkThru#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#6)]  
  
## <a name="exporting-a-public-key"></a><span data-ttu-id="29bd0-188">Eksportowanie klucza publicznego</span><span class="sxs-lookup"><span data-stu-id="29bd0-188">Exporting a Public Key</span></span>  
 <span data-ttu-id="29bd0-189">To zadanie służy do zapisywania klucza utworzonego za pomocą przycisku `Create Keys` do pliku.</span><span class="sxs-lookup"><span data-stu-id="29bd0-189">This task saves the key created by the `Create Keys` button to a file.</span></span> <span data-ttu-id="29bd0-190">Eksportuje tylko parametry publiczne.</span><span class="sxs-lookup"><span data-stu-id="29bd0-190">It exports only the public parameters.</span></span>  
  
 <span data-ttu-id="29bd0-191">To zadanie symuluje scenariusz dla Alicja przekazującej Roberta swój klucz publiczny, aby mógł szyfrować pliki.</span><span class="sxs-lookup"><span data-stu-id="29bd0-191">This task simulates the scenario of Alice giving Bob her public key so that he can encrypt files for her.</span></span> <span data-ttu-id="29bd0-192">Osoby, które mają ten klucz publiczny, nie będą w stanie odszyfrować, ponieważ nie mają pełnej pary kluczy z parametrami prywatnymi.</span><span class="sxs-lookup"><span data-stu-id="29bd0-192">He and others who have that public key will not be able to decrypt them because they do not have the full key pair with private parameters.</span></span>  
  
 <span data-ttu-id="29bd0-193">Dodaj następujący kod jako procedurę obsługi zdarzeń `Click` dla przycisku `Export Public Key` (`buttonExportPublicKey_Click`).</span><span class="sxs-lookup"><span data-stu-id="29bd0-193">Add the following code as the `Click` event handler for the `Export Public Key` button (`buttonExportPublicKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#8)]
 [!code-vb[CryptoWalkThru#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#8)]  
  
## <a name="importing-a-public-key"></a><span data-ttu-id="29bd0-194">Importowanie klucza publicznego</span><span class="sxs-lookup"><span data-stu-id="29bd0-194">Importing a Public Key</span></span>  
 <span data-ttu-id="29bd0-195">To zadanie ładuje klucz z tylko parametrami publicznymi, utworzonym przez przycisk `Export Public Key` i ustawia go jako nazwę kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="29bd0-195">This task loads the key with only public parameters, as created by the `Export Public Key` button, and sets it as the key container name.</span></span>  
  
 <span data-ttu-id="29bd0-196">To zadanie symuluje scenariusz ładowania klucza Alicja z tylko parametrami publicznymi, dzięki czemu może zaszyfrować pliki.</span><span class="sxs-lookup"><span data-stu-id="29bd0-196">This task simulates the scenario of Bob loading Alice's key with only public parameters so he can encrypt files for her.</span></span>  
  
 <span data-ttu-id="29bd0-197">Dodaj następujący kod jako procedurę obsługi zdarzeń `Click` dla przycisku `Import Public Key` (`buttonImportPublicKey_Click`).</span><span class="sxs-lookup"><span data-stu-id="29bd0-197">Add the following code as the `Click` event handler for the `Import Public Key` button (`buttonImportPublicKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#9)]
 [!code-vb[CryptoWalkThru#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#9)]  
  
## <a name="getting-a-private-key"></a><span data-ttu-id="29bd0-198">Pobieranie klucza prywatnego</span><span class="sxs-lookup"><span data-stu-id="29bd0-198">Getting a Private Key</span></span>  
 <span data-ttu-id="29bd0-199">To zadanie ustawia nazwę kontenera kluczy na nazwę klucza utworzonego przy użyciu przycisku `Create Keys`.</span><span class="sxs-lookup"><span data-stu-id="29bd0-199">This task sets the key container name to the name of the key created by using the `Create Keys` button.</span></span> <span data-ttu-id="29bd0-200">Kontener kluczy będzie zawierać pełną parę kluczy z parametrami prywatnymi.</span><span class="sxs-lookup"><span data-stu-id="29bd0-200">The key container will contain the full key pair with private parameters.</span></span>  
  
 <span data-ttu-id="29bd0-201">To zadanie symuluje scenariusz Alicja przy użyciu klucza prywatnego w celu odszyfrowania plików zaszyfrowanych przez Robert.</span><span class="sxs-lookup"><span data-stu-id="29bd0-201">This task simulates the scenario of Alice using her private key to decrypt files encrypted by Bob.</span></span>  
  
 <span data-ttu-id="29bd0-202">Dodaj następujący kod jako procedurę obsługi zdarzeń `Click` dla przycisku `Get Private Key` (`buttonGetPrivateKey_Click`).</span><span class="sxs-lookup"><span data-stu-id="29bd0-202">Add the following code as the `Click` event handler for the `Get Private Key` button (`buttonGetPrivateKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#7)]
 [!code-vb[CryptoWalkThru#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#7)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="29bd0-203">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="29bd0-203">Testing the Application</span></span>  
 <span data-ttu-id="29bd0-204">Po skompilowaniu aplikacji wykonaj następujące scenariusze testowania.</span><span class="sxs-lookup"><span data-stu-id="29bd0-204">After you have built the application, perform the following testing scenarios.</span></span>  
  
#### <a name="to-create-keys-encrypt-and-decrypt"></a><span data-ttu-id="29bd0-205">Aby utworzyć klucze, szyfrowanie i odszyfrowywanie</span><span class="sxs-lookup"><span data-stu-id="29bd0-205">To create keys, encrypt, and decrypt</span></span>  
  
1. <span data-ttu-id="29bd0-206">Kliknij przycisk `Create Keys`.</span><span class="sxs-lookup"><span data-stu-id="29bd0-206">Click the `Create Keys` button.</span></span> <span data-ttu-id="29bd0-207">Etykieta Wyświetla nazwę klucza i pokazuje, że jest to pełna para kluczy.</span><span class="sxs-lookup"><span data-stu-id="29bd0-207">The label displays the key name and shows that it is a full key pair.</span></span>  
  
2. <span data-ttu-id="29bd0-208">Kliknij przycisk `Export Public Key`.</span><span class="sxs-lookup"><span data-stu-id="29bd0-208">Click the `Export Public Key` button.</span></span> <span data-ttu-id="29bd0-209">Należy zauważyć, że eksportowanie parametrów klucza publicznego nie zmienia bieżącego klucza.</span><span class="sxs-lookup"><span data-stu-id="29bd0-209">Note that exporting the public key parameters does not change the current key.</span></span>  
  
3. <span data-ttu-id="29bd0-210">Kliknij przycisk `Encrypt File` i wybierz plik.</span><span class="sxs-lookup"><span data-stu-id="29bd0-210">Click the `Encrypt File` button and select a file.</span></span>  
  
4. <span data-ttu-id="29bd0-211">Kliknij przycisk `Decrypt File` i wybierz plik, który został zaszyfrowany.</span><span class="sxs-lookup"><span data-stu-id="29bd0-211">Click the `Decrypt File` button and select the file just encrypted.</span></span>  
  
5. <span data-ttu-id="29bd0-212">Zapoznaj się z odszyfrowaniem pliku.</span><span class="sxs-lookup"><span data-stu-id="29bd0-212">Examine the file just decrypted.</span></span>  
  
6. <span data-ttu-id="29bd0-213">Zamknij aplikację i uruchom ją ponownie, aby przetestować pobieranie utrwalonych kontenerów kluczy w następnym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="29bd0-213">Close the application and restart it to test retrieving persisted key containers in the next scenario.</span></span>  
  
#### <a name="to-encrypt-using-the-public-key"></a><span data-ttu-id="29bd0-214">Aby zaszyfrować przy użyciu klucza publicznego</span><span class="sxs-lookup"><span data-stu-id="29bd0-214">To encrypt using the public key</span></span>  
  
1. <span data-ttu-id="29bd0-215">Kliknij przycisk `Import Public Key`.</span><span class="sxs-lookup"><span data-stu-id="29bd0-215">Click the `Import Public Key` button.</span></span> <span data-ttu-id="29bd0-216">Etykieta Wyświetla nazwę klucza i pokazuje, że jest tylko publiczna.</span><span class="sxs-lookup"><span data-stu-id="29bd0-216">The label displays the key name and shows that it is public only.</span></span>  
  
2. <span data-ttu-id="29bd0-217">Kliknij przycisk `Encrypt File` i wybierz plik.</span><span class="sxs-lookup"><span data-stu-id="29bd0-217">Click the `Encrypt File` button and select a file.</span></span>  
  
3. <span data-ttu-id="29bd0-218">Kliknij przycisk `Decrypt File` i wybierz plik, który został zaszyfrowany.</span><span class="sxs-lookup"><span data-stu-id="29bd0-218">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="29bd0-219">Nie powiedzie się, ponieważ musisz mieć klucz prywatny do odszyfrowania.</span><span class="sxs-lookup"><span data-stu-id="29bd0-219">This will fail because you must have the private key to decrypt.</span></span>  
  
 <span data-ttu-id="29bd0-220">W tym scenariuszu przedstawiono tylko klucz publiczny do szyfrowania pliku dla innej osoby.</span><span class="sxs-lookup"><span data-stu-id="29bd0-220">This scenario demonstrates having only the public key to encrypt a file for another person.</span></span> <span data-ttu-id="29bd0-221">Zwykle osoba ta może uzyskać tylko klucz publiczny i wstrzymać klucz prywatny do odszyfrowania.</span><span class="sxs-lookup"><span data-stu-id="29bd0-221">Typically that person would give you only the public key and withhold the private key for decryption.</span></span>  
  
#### <a name="to-decrypt-using-the-private-key"></a><span data-ttu-id="29bd0-222">Aby odszyfrować przy użyciu klucza prywatnego</span><span class="sxs-lookup"><span data-stu-id="29bd0-222">To decrypt using the private key</span></span>  
  
1. <span data-ttu-id="29bd0-223">Kliknij przycisk `Get Private Key`.</span><span class="sxs-lookup"><span data-stu-id="29bd0-223">Click the `Get Private Key` button.</span></span> <span data-ttu-id="29bd0-224">Etykieta Wyświetla nazwę klucza i pokazuje, czy jest to pełna para kluczy.</span><span class="sxs-lookup"><span data-stu-id="29bd0-224">The label displays the key name and shows whether it is the full key pair.</span></span>  
  
2. <span data-ttu-id="29bd0-225">Kliknij przycisk `Decrypt File` i wybierz plik, który został zaszyfrowany.</span><span class="sxs-lookup"><span data-stu-id="29bd0-225">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="29bd0-226">Ta operacja zakończy się pomyślnie, ponieważ masz pełną parę kluczy do odszyfrowania.</span><span class="sxs-lookup"><span data-stu-id="29bd0-226">This will be successful because you have the full key pair to decrypt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29bd0-227">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="29bd0-227">See also</span></span>

- [<span data-ttu-id="29bd0-228">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="29bd0-228">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
