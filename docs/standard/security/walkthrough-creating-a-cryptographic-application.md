---
title: 'Wskazówki: tworzenie aplikacji kryptograficznej'
description: Zapoznaj się z tworzeniem aplikacji kryptograficznej. Dowiedz się, jak szyfrować i odszyfrowywać zawartość w aplikacji Windows Forms.
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
ms.openlocfilehash: 72116227fbec2435d428ad2bbdb4cc74e5c3663f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602183"
---
# <a name="walkthrough-creating-a-cryptographic-application"></a><span data-ttu-id="17feb-104">Wskazówki: tworzenie aplikacji kryptograficznej</span><span class="sxs-lookup"><span data-stu-id="17feb-104">Walkthrough: Creating a Cryptographic Application</span></span>
<span data-ttu-id="17feb-105">W tym instruktażu pokazano, jak szyfrować i odszyfrowywać zawartość.</span><span class="sxs-lookup"><span data-stu-id="17feb-105">This walkthrough demonstrates how to encrypt and decrypt content.</span></span> <span data-ttu-id="17feb-106">Przykłady kodu są przeznaczone dla aplikacji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="17feb-106">The code examples are designed for a Windows Forms application.</span></span> <span data-ttu-id="17feb-107">Ta aplikacja nie pokazuje rzeczywistych scenariuszy, takich jak korzystanie z kart inteligentnych.</span><span class="sxs-lookup"><span data-stu-id="17feb-107">This application does not demonstrate real world scenarios, such as using smart cards.</span></span> <span data-ttu-id="17feb-108">Zamiast tego pokazuje podstawowe informacje dotyczące szyfrowania i odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="17feb-108">Instead, it demonstrates the fundamentals of encryption and decryption.</span></span>  
  
 <span data-ttu-id="17feb-109">W tym instruktażu zastosowano następujące wytyczne dotyczące szyfrowania:</span><span class="sxs-lookup"><span data-stu-id="17feb-109">This walkthrough uses the following guidelines for encryption:</span></span>  
  
- <span data-ttu-id="17feb-110">Użyj <xref:System.Security.Cryptography.RijndaelManaged> klasy, algorytmu symetrycznego, aby szyfrować i odszyfrowywać dane przy użyciu automatycznie wygenerowanego <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> i <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A> .</span><span class="sxs-lookup"><span data-stu-id="17feb-110">Use the <xref:System.Security.Cryptography.RijndaelManaged> class, a symmetric algorithm, to encrypt and decrypt data by using its automatically generated <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> and <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>.</span></span>  
  
- <span data-ttu-id="17feb-111">Użyj <xref:System.Security.Cryptography.RSACryptoServiceProvider> algorytmu asymetrycznego, aby szyfrować i odszyfrowywać klucz do danych szyfrowanych przez program <xref:System.Security.Cryptography.RijndaelManaged> .</span><span class="sxs-lookup"><span data-stu-id="17feb-111">Use the <xref:System.Security.Cryptography.RSACryptoServiceProvider>, an asymmetric algorithm, to encrypt and decrypt the key to the data encrypted by <xref:System.Security.Cryptography.RijndaelManaged>.</span></span> <span data-ttu-id="17feb-112">Algorytmy asymetryczne najlepiej używać w przypadku mniejszych ilości danych, takich jak klucz.</span><span class="sxs-lookup"><span data-stu-id="17feb-112">Asymmetric algorithms are best used for smaller amounts of data, such as a key.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="17feb-113">Jeśli chcesz chronić dane na komputerze zamiast wymieniać zaszyfrowaną zawartość z innymi osobami, rozważ użycie <xref:System.Security.Cryptography.ProtectedData> <xref:System.Security.Cryptography.ProtectedMemory> klas lub.</span><span class="sxs-lookup"><span data-stu-id="17feb-113">If you want to protect data on your computer instead of exchanging encrypted content with other people, consider using the <xref:System.Security.Cryptography.ProtectedData> or <xref:System.Security.Cryptography.ProtectedMemory> classes.</span></span>  
  
 <span data-ttu-id="17feb-114">Poniższa tabela zawiera podsumowanie zadań kryptograficznych w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="17feb-114">The following table summarizes the cryptographic tasks in this topic.</span></span>  
  
|<span data-ttu-id="17feb-115">Zadanie</span><span class="sxs-lookup"><span data-stu-id="17feb-115">Task</span></span>|<span data-ttu-id="17feb-116">Opis</span><span class="sxs-lookup"><span data-stu-id="17feb-116">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="17feb-117">Tworzenie aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="17feb-117">Creating a Windows Forms application</span></span>|<span data-ttu-id="17feb-118">Wyświetla listę kontrolek, które są wymagane do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="17feb-118">Lists the controls that are required to run the application.</span></span>|  
|<span data-ttu-id="17feb-119">Deklarowanie obiektów globalnych</span><span class="sxs-lookup"><span data-stu-id="17feb-119">Declaring global objects</span></span>|<span data-ttu-id="17feb-120">Deklaruje zmienne ścieżki ciągów, <xref:System.Security.Cryptography.CspParameters> i i ma <xref:System.Security.Cryptography.RSACryptoServiceProvider> kontekst globalny <xref:System.Windows.Forms.Form> klasy.</span><span class="sxs-lookup"><span data-stu-id="17feb-120">Declares string path variables, the <xref:System.Security.Cryptography.CspParameters>, and the <xref:System.Security.Cryptography.RSACryptoServiceProvider> to have global context of the <xref:System.Windows.Forms.Form> class.</span></span>|  
|<span data-ttu-id="17feb-121">Tworzenie klucza asymetrycznego</span><span class="sxs-lookup"><span data-stu-id="17feb-121">Creating an asymmetric key</span></span>|<span data-ttu-id="17feb-122">Tworzy asymetryczną parę wartości klucza publicznego i prywatnego i przypisuje mu nazwę kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="17feb-122">Creates an asymmetric public and private key value pair and assigns it a key container name.</span></span>|  
|<span data-ttu-id="17feb-123">Szyfrowanie pliku</span><span class="sxs-lookup"><span data-stu-id="17feb-123">Encrypting a file</span></span>|<span data-ttu-id="17feb-124">Wyświetla okno dialogowe, w którym można wybrać plik do szyfrowania i szyfruje plik.</span><span class="sxs-lookup"><span data-stu-id="17feb-124">Displays a dialog box to select a file for encryption and encrypts the file.</span></span>|  
|<span data-ttu-id="17feb-125">Odszyfrowywanie pliku</span><span class="sxs-lookup"><span data-stu-id="17feb-125">Decrypting a file</span></span>|<span data-ttu-id="17feb-126">Wyświetla okno dialogowe, w którym można wybrać zaszyfrowany plik do odszyfrowania i odszyfrować plik.</span><span class="sxs-lookup"><span data-stu-id="17feb-126">Displays a dialog box to select an encrypted file for decryption and decrypts the file.</span></span>|  
|<span data-ttu-id="17feb-127">Pobieranie klucza prywatnego</span><span class="sxs-lookup"><span data-stu-id="17feb-127">Getting a private key</span></span>|<span data-ttu-id="17feb-128">Pobiera pełną parę kluczy przy użyciu nazwy kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="17feb-128">Gets the full key pair using the key container name.</span></span>|  
|<span data-ttu-id="17feb-129">Eksportowanie klucza publicznego</span><span class="sxs-lookup"><span data-stu-id="17feb-129">Exporting a public key</span></span>|<span data-ttu-id="17feb-130">Zapisuje klucz do pliku XML tylko z parametrami publicznymi.</span><span class="sxs-lookup"><span data-stu-id="17feb-130">Saves the key to an XML file with only public parameters.</span></span>|  
|<span data-ttu-id="17feb-131">Importowanie klucza publicznego</span><span class="sxs-lookup"><span data-stu-id="17feb-131">Importing a public key</span></span>|<span data-ttu-id="17feb-132">Ładuje klucz z pliku XML do kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="17feb-132">Loads the key from an XML file into the key container.</span></span>|  
|<span data-ttu-id="17feb-133">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="17feb-133">Testing the application</span></span>|<span data-ttu-id="17feb-134">Wyświetla listę procedur testowania tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="17feb-134">Lists procedures for testing this application.</span></span>|  
  
## <a name="prerequisites"></a><span data-ttu-id="17feb-135">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="17feb-135">Prerequisites</span></span>  
 <span data-ttu-id="17feb-136">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="17feb-136">You need the following components to complete this walkthrough:</span></span>  
  
- <span data-ttu-id="17feb-137">Odwołania do <xref:System.IO> <xref:System.Security.Cryptography> przestrzeni nazw i.</span><span class="sxs-lookup"><span data-stu-id="17feb-137">References to the <xref:System.IO> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
## <a name="creating-a-windows-forms-application"></a><span data-ttu-id="17feb-138">Tworzenie aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="17feb-138">Creating a Windows Forms Application</span></span>  
 <span data-ttu-id="17feb-139">Większość przykładów kodu w tym instruktażu została zaprojektowana jako programy obsługi zdarzeń dla kontrolek Button.</span><span class="sxs-lookup"><span data-stu-id="17feb-139">Most of the code examples in this walkthrough are designed to be event handlers for button controls.</span></span> <span data-ttu-id="17feb-140">Poniższa tabela zawiera listę formantów wymaganych dla przykładowej aplikacji i ich wymaganych nazw w celu dopasowania do przykładów kodu.</span><span class="sxs-lookup"><span data-stu-id="17feb-140">The following table lists the controls required for the sample application and their required names to match the code examples.</span></span>  
  
|<span data-ttu-id="17feb-141">Kontrola</span><span class="sxs-lookup"><span data-stu-id="17feb-141">Control</span></span>|<span data-ttu-id="17feb-142">Nazwa</span><span class="sxs-lookup"><span data-stu-id="17feb-142">Name</span></span>|<span data-ttu-id="17feb-143">Właściwość Text (zgodnie z wymaganiami)</span><span class="sxs-lookup"><span data-stu-id="17feb-143">Text property (as needed)</span></span>|  
|-------------|----------|---------------------------------|  
|<xref:System.Windows.Forms.Button>|`buttonEncryptFile`|<span data-ttu-id="17feb-144">Szyfruj plik</span><span class="sxs-lookup"><span data-stu-id="17feb-144">Encrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonDecryptFile`|<span data-ttu-id="17feb-145">Odszyfruj plik</span><span class="sxs-lookup"><span data-stu-id="17feb-145">Decrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonCreateAsmKeys`|<span data-ttu-id="17feb-146">Utwórz klucze</span><span class="sxs-lookup"><span data-stu-id="17feb-146">Create Keys</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonExportPublicKey`|<span data-ttu-id="17feb-147">Eksportuj klucz publiczny</span><span class="sxs-lookup"><span data-stu-id="17feb-147">Export Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonImportPublicKey`|<span data-ttu-id="17feb-148">Importuj klucz publiczny</span><span class="sxs-lookup"><span data-stu-id="17feb-148">Import Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonGetPrivateKey`|<span data-ttu-id="17feb-149">Pobierz klucz prywatny</span><span class="sxs-lookup"><span data-stu-id="17feb-149">Get Private Key</span></span>|  
|<xref:System.Windows.Forms.Label>|`label1`|<span data-ttu-id="17feb-150">Nie ustawiono klucza</span><span class="sxs-lookup"><span data-stu-id="17feb-150">Key not set</span></span>|  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog2`||  
  
 <span data-ttu-id="17feb-151">Kliknij dwukrotnie przyciski w projektancie programu Visual Studio, aby utworzyć obsługę zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="17feb-151">Double-click the buttons in the  Visual Studio designer to create their event handlers.</span></span>  
  
## <a name="declaring-global-objects"></a><span data-ttu-id="17feb-152">Deklarowanie obiektów globalnych</span><span class="sxs-lookup"><span data-stu-id="17feb-152">Declaring Global Objects</span></span>  
 <span data-ttu-id="17feb-153">Dodaj następujący kod do konstruktora formularza.</span><span class="sxs-lookup"><span data-stu-id="17feb-153">Add the following code to the Form's constructor.</span></span> <span data-ttu-id="17feb-154">Edytuj zmienne ciągów dla środowiska i preferencji.</span><span class="sxs-lookup"><span data-stu-id="17feb-154">Edit the string variables for your environment and preferences.</span></span>  
  
 [!code-csharp[CryptoWalkThru#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#1)]
 [!code-vb[CryptoWalkThru#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#1)]  
  
## <a name="creating-an-asymmetric-key"></a><span data-ttu-id="17feb-155">Tworzenie klucza asymetrycznego</span><span class="sxs-lookup"><span data-stu-id="17feb-155">Creating an Asymmetric Key</span></span>  
 <span data-ttu-id="17feb-156">To zadanie tworzy klucz asymetryczny, który szyfruje i odszyfrowuje <xref:System.Security.Cryptography.RijndaelManaged> klucz.</span><span class="sxs-lookup"><span data-stu-id="17feb-156">This task creates an asymmetric key that encrypts and decrypts the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span> <span data-ttu-id="17feb-157">Ten klucz został użyty do zaszyfrowania zawartości i wyświetla nazwę kontenera kluczy w kontrolce etykieta.</span><span class="sxs-lookup"><span data-stu-id="17feb-157">This key was used to encrypt the content and it displays the key container name on the label control.</span></span>  
  
 <span data-ttu-id="17feb-158">Dodaj następujący kod jako `Click` procedurę obsługi zdarzeń dla `Create Keys` przycisku ( `buttonCreateAsmKeys_Click` ).</span><span class="sxs-lookup"><span data-stu-id="17feb-158">Add the following code as the `Click` event handler for the `Create Keys` button (`buttonCreateAsmKeys_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#2)]
 [!code-vb[CryptoWalkThru#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#2)]  
  
## <a name="encrypting-a-file"></a><span data-ttu-id="17feb-159">Szyfrowanie pliku</span><span class="sxs-lookup"><span data-stu-id="17feb-159">Encrypting a File</span></span>  
 <span data-ttu-id="17feb-160">To zadanie obejmuje dwie metody: metoda obsługi zdarzeń dla `Encrypt File` przycisku ( `buttonEncryptFile_Click` ) i `EncryptFile` metody.</span><span class="sxs-lookup"><span data-stu-id="17feb-160">This task involves two methods: the event handler method for the `Encrypt File` button (`buttonEncryptFile_Click`) and the `EncryptFile` method.</span></span> <span data-ttu-id="17feb-161">Pierwsza metoda wyświetla okno dialogowe, w którym można wybrać plik i przekazuje nazwę pliku do drugiej metody, która wykonuje szyfrowanie.</span><span class="sxs-lookup"><span data-stu-id="17feb-161">The first method displays a dialog box for selecting a file and passes the file name to the second method, which performs the encryption.</span></span>  
  
 <span data-ttu-id="17feb-162">Zaszyfrowana zawartość, klucz i IV są zapisywane na jednym <xref:System.IO.FileStream> , który jest nazywany Pakietem szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="17feb-162">The encrypted content, key, and IV are all saved to one <xref:System.IO.FileStream>, which is referred to as the encryption package.</span></span>  
  
 <span data-ttu-id="17feb-163">`EncryptFile`Metoda wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="17feb-163">The `EncryptFile` method does the following:</span></span>  
  
1. <span data-ttu-id="17feb-164">Tworzy <xref:System.Security.Cryptography.RijndaelManaged> algorytm symetryczny do szyfrowania zawartości.</span><span class="sxs-lookup"><span data-stu-id="17feb-164">Creates a <xref:System.Security.Cryptography.RijndaelManaged> symmetric algorithm to encrypt the content.</span></span>  
  
2. <span data-ttu-id="17feb-165">Tworzy obiekt służący <xref:System.Security.Cryptography.RSACryptoServiceProvider> do szyfrowania <xref:System.Security.Cryptography.RijndaelManaged> klucza.</span><span class="sxs-lookup"><span data-stu-id="17feb-165">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to encrypt the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span>  
  
3. <span data-ttu-id="17feb-166">Używa <xref:System.Security.Cryptography.CryptoStream> obiektu do odczytu i szyfrowania <xref:System.IO.FileStream> pliku źródłowego w blokach bajtów do <xref:System.IO.FileStream> obiektu docelowego dla zaszyfrowanego pliku.</span><span class="sxs-lookup"><span data-stu-id="17feb-166">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and encrypt the <xref:System.IO.FileStream> of the source file, in blocks of bytes, into a destination <xref:System.IO.FileStream> object for the encrypted file.</span></span>  
  
4. <span data-ttu-id="17feb-167">Określa długość zaszyfrowanego klucza i IV i tworzy tablicę bajtową wartości ich długości.</span><span class="sxs-lookup"><span data-stu-id="17feb-167">Determines the lengths of the encrypted key and IV, and creates byte arrays of their length values.</span></span>  
  
5. <span data-ttu-id="17feb-168">Zapisuje wartości key, IV i ich długości do zaszyfrowanego pakietu.</span><span class="sxs-lookup"><span data-stu-id="17feb-168">Writes the Key, IV, and their length values to the encrypted package.</span></span>  
  
 <span data-ttu-id="17feb-169">Pakiet szyfrowania używa następującego formatu:</span><span class="sxs-lookup"><span data-stu-id="17feb-169">The encryption package uses the following format:</span></span>  
  
- <span data-ttu-id="17feb-170">Długość klucza, bajty 0-3</span><span class="sxs-lookup"><span data-stu-id="17feb-170">Key length, bytes 0 - 3</span></span>  
  
- <span data-ttu-id="17feb-171">Długość IV, bajtów 4-7</span><span class="sxs-lookup"><span data-stu-id="17feb-171">IV length, bytes 4 - 7</span></span>  
  
- <span data-ttu-id="17feb-172">Zaszyfrowany klucz</span><span class="sxs-lookup"><span data-stu-id="17feb-172">Encrypted key</span></span>  
  
- <span data-ttu-id="17feb-173">V</span><span class="sxs-lookup"><span data-stu-id="17feb-173">IV</span></span>  
  
- <span data-ttu-id="17feb-174">Szyfrowanie tekstu</span><span class="sxs-lookup"><span data-stu-id="17feb-174">Cipher text</span></span>  
  
 <span data-ttu-id="17feb-175">Możesz użyć długości klucza i IV, aby określić punkty początkowe i długości wszystkich części pakietu szyfrującego, które mogą być następnie użyte do odszyfrowania pliku.</span><span class="sxs-lookup"><span data-stu-id="17feb-175">You can use the lengths of the key and IV to determine the starting points and lengths of all parts of the encryption package, which can then be used to decrypt the file.</span></span>  
  
 <span data-ttu-id="17feb-176">Dodaj następujący kod jako `Click` procedurę obsługi zdarzeń dla `Encrypt File` przycisku ( `buttonEncryptFile_Click` ).</span><span class="sxs-lookup"><span data-stu-id="17feb-176">Add the following code as the `Click` event handler for the `Encrypt File` button (`buttonEncryptFile_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#3)]
 [!code-vb[CryptoWalkThru#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#3)]  
  
 <span data-ttu-id="17feb-177">Dodaj następującą `EncryptFile` metodę do formularza.</span><span class="sxs-lookup"><span data-stu-id="17feb-177">Add the following `EncryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#5)]
 [!code-vb[CryptoWalkThru#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#5)]  
  
## <a name="decrypting-a-file"></a><span data-ttu-id="17feb-178">Odszyfrowywanie pliku</span><span class="sxs-lookup"><span data-stu-id="17feb-178">Decrypting a File</span></span>  
 <span data-ttu-id="17feb-179">To zadanie obejmuje dwie metody, metodę obsługi zdarzeń dla `Decrypt File` przycisku ( `buttonDecryptFile_Click` ) i `DecryptFile` metodę.</span><span class="sxs-lookup"><span data-stu-id="17feb-179">This task involves two methods, the event handler method for the `Decrypt File` button (`buttonDecryptFile_Click`), and the `DecryptFile` method.</span></span> <span data-ttu-id="17feb-180">Pierwsza metoda wyświetla okno dialogowe, w którym można wybrać plik i przekazuje jego nazwę pliku do drugiej metody, która wykonuje odszyfrowywanie.</span><span class="sxs-lookup"><span data-stu-id="17feb-180">The first method displays a dialog box for selecting a file and passes its file name to the second method, which performs the decryption.</span></span>  
  
 <span data-ttu-id="17feb-181">`Decrypt`Metoda wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="17feb-181">The `Decrypt` method does the following:</span></span>  
  
1. <span data-ttu-id="17feb-182">Tworzy <xref:System.Security.Cryptography.RijndaelManaged> algorytm symetryczny służący do odszyfrowywania zawartości.</span><span class="sxs-lookup"><span data-stu-id="17feb-182">Creates a <xref:System.Security.Cryptography.RijndaelManaged> symmetric algorithm to decrypt the content.</span></span>  
  
2. <span data-ttu-id="17feb-183">Odczytuje pierwsze osiem bajtów <xref:System.IO.FileStream> zaszyfrowanego pakietu do tablic bajtów w celu uzyskania długości zaszyfrowanego klucza i IV.</span><span class="sxs-lookup"><span data-stu-id="17feb-183">Reads the first eight bytes of the <xref:System.IO.FileStream> of the encrypted package into byte arrays to obtain the lengths of the encrypted key and the IV.</span></span>  
  
3. <span data-ttu-id="17feb-184">Wyodrębnia klucz i IV z pakietu szyfrowania do tablic bajtowych.</span><span class="sxs-lookup"><span data-stu-id="17feb-184">Extracts the key and IV from the encryption package into byte arrays.</span></span>  
  
4. <span data-ttu-id="17feb-185">Tworzy <xref:System.Security.Cryptography.RSACryptoServiceProvider> obiekt do odszyfrowania <xref:System.Security.Cryptography.RijndaelManaged> klucza.</span><span class="sxs-lookup"><span data-stu-id="17feb-185">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to decrypt the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span>  
  
5. <span data-ttu-id="17feb-186">Używa <xref:System.Security.Cryptography.CryptoStream> obiektu do odczytywania i odszyfrowywania sekcji szyfrowania tekstu <xref:System.IO.FileStream> pakietu szyfrowania w blokach bajtów do <xref:System.IO.FileStream> obiektu w odszyfrowanym pliku.</span><span class="sxs-lookup"><span data-stu-id="17feb-186">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and decrypt the cipher text section of the <xref:System.IO.FileStream> encryption package, in blocks of bytes, into the <xref:System.IO.FileStream> object for the decrypted file.</span></span> <span data-ttu-id="17feb-187">Po zakończeniu odszyfrowywania zostanie zakończone.</span><span class="sxs-lookup"><span data-stu-id="17feb-187">When this is finished, the decryption is completed.</span></span>  
  
 <span data-ttu-id="17feb-188">Dodaj następujący kod jako `Click` procedurę obsługi zdarzeń dla `Decrypt File` przycisku.</span><span class="sxs-lookup"><span data-stu-id="17feb-188">Add the following code as the `Click` event handler for the `Decrypt File` button.</span></span>  
  
 [!code-csharp[CryptoWalkThru#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#4)]
 [!code-vb[CryptoWalkThru#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#4)]  
  
 <span data-ttu-id="17feb-189">Dodaj następującą `DecryptFile` metodę do formularza.</span><span class="sxs-lookup"><span data-stu-id="17feb-189">Add the following `DecryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#6)]
 [!code-vb[CryptoWalkThru#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#6)]  
  
## <a name="exporting-a-public-key"></a><span data-ttu-id="17feb-190">Eksportowanie klucza publicznego</span><span class="sxs-lookup"><span data-stu-id="17feb-190">Exporting a Public Key</span></span>  
 <span data-ttu-id="17feb-191">To zadanie służy do zapisywania klucza utworzonego przez `Create Keys` przycisk do pliku.</span><span class="sxs-lookup"><span data-stu-id="17feb-191">This task saves the key created by the `Create Keys` button to a file.</span></span> <span data-ttu-id="17feb-192">Eksportuje tylko parametry publiczne.</span><span class="sxs-lookup"><span data-stu-id="17feb-192">It exports only the public parameters.</span></span>  
  
 <span data-ttu-id="17feb-193">To zadanie symuluje scenariusz dla Alicja przekazującej Roberta swój klucz publiczny, aby mógł szyfrować pliki.</span><span class="sxs-lookup"><span data-stu-id="17feb-193">This task simulates the scenario of Alice giving Bob her public key so that he can encrypt files for her.</span></span> <span data-ttu-id="17feb-194">Osoby, które mają ten klucz publiczny, nie będą w stanie odszyfrować, ponieważ nie mają pełnej pary kluczy z parametrami prywatnymi.</span><span class="sxs-lookup"><span data-stu-id="17feb-194">He and others who have that public key will not be able to decrypt them because they do not have the full key pair with private parameters.</span></span>  
  
 <span data-ttu-id="17feb-195">Dodaj następujący kod jako `Click` procedurę obsługi zdarzeń dla `Export Public Key` przycisku ( `buttonExportPublicKey_Click` ).</span><span class="sxs-lookup"><span data-stu-id="17feb-195">Add the following code as the `Click` event handler for the `Export Public Key` button (`buttonExportPublicKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#8)]
 [!code-vb[CryptoWalkThru#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#8)]  
  
## <a name="importing-a-public-key"></a><span data-ttu-id="17feb-196">Importowanie klucza publicznego</span><span class="sxs-lookup"><span data-stu-id="17feb-196">Importing a Public Key</span></span>  
 <span data-ttu-id="17feb-197">To zadanie ładuje klucz z tylko parametrami publicznymi, utworzonym przez `Export Public Key` przycisk i ustawia go jako nazwę kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="17feb-197">This task loads the key with only public parameters, as created by the `Export Public Key` button, and sets it as the key container name.</span></span>  
  
 <span data-ttu-id="17feb-198">To zadanie symuluje scenariusz ładowania klucza Alicja z tylko parametrami publicznymi, dzięki czemu może zaszyfrować pliki.</span><span class="sxs-lookup"><span data-stu-id="17feb-198">This task simulates the scenario of Bob loading Alice's key with only public parameters so he can encrypt files for her.</span></span>  
  
 <span data-ttu-id="17feb-199">Dodaj następujący kod jako `Click` procedurę obsługi zdarzeń dla `Import Public Key` przycisku ( `buttonImportPublicKey_Click` ).</span><span class="sxs-lookup"><span data-stu-id="17feb-199">Add the following code as the `Click` event handler for the `Import Public Key` button (`buttonImportPublicKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#9)]
 [!code-vb[CryptoWalkThru#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#9)]  
  
## <a name="getting-a-private-key"></a><span data-ttu-id="17feb-200">Pobieranie klucza prywatnego</span><span class="sxs-lookup"><span data-stu-id="17feb-200">Getting a Private Key</span></span>  
 <span data-ttu-id="17feb-201">To zadanie ustawia nazwę kontenera kluczy na nazwę klucza utworzonego za pomocą `Create Keys` przycisku.</span><span class="sxs-lookup"><span data-stu-id="17feb-201">This task sets the key container name to the name of the key created by using the `Create Keys` button.</span></span> <span data-ttu-id="17feb-202">Kontener kluczy będzie zawierać pełną parę kluczy z parametrami prywatnymi.</span><span class="sxs-lookup"><span data-stu-id="17feb-202">The key container will contain the full key pair with private parameters.</span></span>  
  
 <span data-ttu-id="17feb-203">To zadanie symuluje scenariusz Alicja przy użyciu klucza prywatnego w celu odszyfrowania plików zaszyfrowanych przez Robert.</span><span class="sxs-lookup"><span data-stu-id="17feb-203">This task simulates the scenario of Alice using her private key to decrypt files encrypted by Bob.</span></span>  
  
 <span data-ttu-id="17feb-204">Dodaj następujący kod jako `Click` procedurę obsługi zdarzeń dla `Get Private Key` przycisku ( `buttonGetPrivateKey_Click` ).</span><span class="sxs-lookup"><span data-stu-id="17feb-204">Add the following code as the `Click` event handler for the `Get Private Key` button (`buttonGetPrivateKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#7)]
 [!code-vb[CryptoWalkThru#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#7)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="17feb-205">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="17feb-205">Testing the Application</span></span>  
 <span data-ttu-id="17feb-206">Po skompilowaniu aplikacji wykonaj następujące scenariusze testowania.</span><span class="sxs-lookup"><span data-stu-id="17feb-206">After you have built the application, perform the following testing scenarios.</span></span>  
  
#### <a name="to-create-keys-encrypt-and-decrypt"></a><span data-ttu-id="17feb-207">Aby utworzyć klucze, szyfrowanie i odszyfrowywanie</span><span class="sxs-lookup"><span data-stu-id="17feb-207">To create keys, encrypt, and decrypt</span></span>  
  
1. <span data-ttu-id="17feb-208">Kliknij przycisk `Create Keys`.</span><span class="sxs-lookup"><span data-stu-id="17feb-208">Click the `Create Keys` button.</span></span> <span data-ttu-id="17feb-209">Etykieta Wyświetla nazwę klucza i pokazuje, że jest to pełna para kluczy.</span><span class="sxs-lookup"><span data-stu-id="17feb-209">The label displays the key name and shows that it is a full key pair.</span></span>  
  
2. <span data-ttu-id="17feb-210">Kliknij przycisk `Export Public Key`.</span><span class="sxs-lookup"><span data-stu-id="17feb-210">Click the `Export Public Key` button.</span></span> <span data-ttu-id="17feb-211">Należy zauważyć, że eksportowanie parametrów klucza publicznego nie zmienia bieżącego klucza.</span><span class="sxs-lookup"><span data-stu-id="17feb-211">Note that exporting the public key parameters does not change the current key.</span></span>  
  
3. <span data-ttu-id="17feb-212">Kliknij `Encrypt File` przycisk i wybierz plik.</span><span class="sxs-lookup"><span data-stu-id="17feb-212">Click the `Encrypt File` button and select a file.</span></span>  
  
4. <span data-ttu-id="17feb-213">Kliknij `Decrypt File` przycisk i wybierz plik, który został zaszyfrowany.</span><span class="sxs-lookup"><span data-stu-id="17feb-213">Click the `Decrypt File` button and select the file just encrypted.</span></span>  
  
5. <span data-ttu-id="17feb-214">Zapoznaj się z odszyfrowaniem pliku.</span><span class="sxs-lookup"><span data-stu-id="17feb-214">Examine the file just decrypted.</span></span>  
  
6. <span data-ttu-id="17feb-215">Zamknij aplikację i uruchom ją ponownie, aby przetestować pobieranie utrwalonych kontenerów kluczy w następnym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="17feb-215">Close the application and restart it to test retrieving persisted key containers in the next scenario.</span></span>  
  
#### <a name="to-encrypt-using-the-public-key"></a><span data-ttu-id="17feb-216">Aby zaszyfrować przy użyciu klucza publicznego</span><span class="sxs-lookup"><span data-stu-id="17feb-216">To encrypt using the public key</span></span>  
  
1. <span data-ttu-id="17feb-217">Kliknij przycisk `Import Public Key`.</span><span class="sxs-lookup"><span data-stu-id="17feb-217">Click the `Import Public Key` button.</span></span> <span data-ttu-id="17feb-218">Etykieta Wyświetla nazwę klucza i pokazuje, że jest tylko publiczna.</span><span class="sxs-lookup"><span data-stu-id="17feb-218">The label displays the key name and shows that it is public only.</span></span>  
  
2. <span data-ttu-id="17feb-219">Kliknij `Encrypt File` przycisk i wybierz plik.</span><span class="sxs-lookup"><span data-stu-id="17feb-219">Click the `Encrypt File` button and select a file.</span></span>  
  
3. <span data-ttu-id="17feb-220">Kliknij `Decrypt File` przycisk i wybierz plik, który został zaszyfrowany.</span><span class="sxs-lookup"><span data-stu-id="17feb-220">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="17feb-221">Nie powiedzie się, ponieważ musisz mieć klucz prywatny do odszyfrowania.</span><span class="sxs-lookup"><span data-stu-id="17feb-221">This will fail because you must have the private key to decrypt.</span></span>  
  
 <span data-ttu-id="17feb-222">W tym scenariuszu przedstawiono tylko klucz publiczny do szyfrowania pliku dla innej osoby.</span><span class="sxs-lookup"><span data-stu-id="17feb-222">This scenario demonstrates having only the public key to encrypt a file for another person.</span></span> <span data-ttu-id="17feb-223">Zwykle osoba ta może uzyskać tylko klucz publiczny i wstrzymać klucz prywatny do odszyfrowania.</span><span class="sxs-lookup"><span data-stu-id="17feb-223">Typically that person would give you only the public key and withhold the private key for decryption.</span></span>  
  
#### <a name="to-decrypt-using-the-private-key"></a><span data-ttu-id="17feb-224">Aby odszyfrować przy użyciu klucza prywatnego</span><span class="sxs-lookup"><span data-stu-id="17feb-224">To decrypt using the private key</span></span>  
  
1. <span data-ttu-id="17feb-225">Kliknij przycisk `Get Private Key`.</span><span class="sxs-lookup"><span data-stu-id="17feb-225">Click the `Get Private Key` button.</span></span> <span data-ttu-id="17feb-226">Etykieta Wyświetla nazwę klucza i pokazuje, czy jest to pełna para kluczy.</span><span class="sxs-lookup"><span data-stu-id="17feb-226">The label displays the key name and shows whether it is the full key pair.</span></span>  
  
2. <span data-ttu-id="17feb-227">Kliknij `Decrypt File` przycisk i wybierz plik, który został zaszyfrowany.</span><span class="sxs-lookup"><span data-stu-id="17feb-227">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="17feb-228">Ta operacja zakończy się pomyślnie, ponieważ masz pełną parę kluczy do odszyfrowania.</span><span class="sxs-lookup"><span data-stu-id="17feb-228">This will be successful because you have the full key pair to decrypt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17feb-229">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="17feb-229">See also</span></span>

- [<span data-ttu-id="17feb-230">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="17feb-230">Cryptographic Services</span></span>](cryptographic-services.md)
