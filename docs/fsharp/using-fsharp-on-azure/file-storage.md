---
title: Rozpoczynanie pracy z usługą Azure File Storage przy użyciu języka F#
description: Usługa Magazyn plików Azure umożliwia przechowywanie plików danych w chmurze oraz instalowanie udziału plików w chmurze z maszyny wirtualnej platformy Azure lub z aplikacji lokalnych działających w systemie Windows.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: d58417e1e3161b958754e01423136a9cdd6a08a6
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75935630"
---
# <a name="get-started-with-azure-file-storage-using-f"></a><span data-ttu-id="7b0b7-103">Rozpoczynanie pracy z usługą Azure File Storage przy użyciu programu F\#</span><span class="sxs-lookup"><span data-stu-id="7b0b7-103">Get started with Azure File storage using F\#</span></span>

<span data-ttu-id="7b0b7-104">Azure File Storage to usługa, która umożliwia korzystanie z udziałów plików w chmurze przy użyciu standardowego [protokołu bloku komunikatów serwera (SMB)](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx).</span><span class="sxs-lookup"><span data-stu-id="7b0b7-104">Azure File storage is a service that offers file shares in the cloud using the standard [Server Message Block (SMB) Protocol](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx).</span></span> <span data-ttu-id="7b0b7-105">Obsługiwane są wersje 2.1 i 3.0 protokołu SMB.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-105">Both SMB 2.1 and SMB 3.0 are supported.</span></span> <span data-ttu-id="7b0b7-106">W usłudze Magazyn plików Azure można migrować starsze aplikacje korzystające z udziałów plików na platformę Azure szybko i bez kosztownych modyfikacji oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-106">With Azure File storage, you can migrate legacy applications that rely on file shares to Azure quickly and without costly rewrites.</span></span> <span data-ttu-id="7b0b7-107">Aplikacje uruchomione na maszynach wirtualnych lub w ramach usług w chmurze platformy Azure, a także na klientach lokalnych mogą instalować udziały plików w chmurze tak samo jak aplikacja na komputerze instalująca typowy udział SMB.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-107">Applications running in Azure virtual machines or cloud services or from on-premises clients can mount a file share in the cloud, just as a desktop application mounts a typical SMB share.</span></span> <span data-ttu-id="7b0b7-108">Dowolna liczba składników aplikacji może następnie równocześnie zainstalować udział Magazynu plików i uzyskiwać do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-108">Any number of application components can then mount and access the File storage share simultaneously.</span></span>

<span data-ttu-id="7b0b7-109">Aby zapoznać się z omówieniem koncepcyjnym usługi File Storage, zobacz [Przewodnik po platformie .NET dotyczący usługi File Storage](/azure/storage/storage-dotnet-how-to-use-files).</span><span class="sxs-lookup"><span data-stu-id="7b0b7-109">For a conceptual overview of file storage, please see [the .NET guide for file storage](/azure/storage/storage-dotnet-how-to-use-files).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7b0b7-110">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="7b0b7-110">Prerequisites</span></span>

<span data-ttu-id="7b0b7-111">Aby skorzystać z tego przewodnika, musisz najpierw [utworzyć konto usługi Azure Storage](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="7b0b7-111">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="7b0b7-112">Wymagany jest również klucz dostępu do magazynu dla tego konta.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-112">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="7b0b7-113">Utwórz F# skrypt i uruchom F# interaktywny</span><span class="sxs-lookup"><span data-stu-id="7b0b7-113">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="7b0b7-114">Przykłady w tym artykule mogą być używane w F# aplikacji lub F# skrypcie.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-114">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="7b0b7-115">Aby utworzyć F# skrypt, Utwórz plik z rozszerzeniem `.fsx`, na przykład `files.fsx`, w środowisku F# deweloperskim.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-115">To create an F# script, create a file with the `.fsx` extension, for example `files.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="7b0b7-116">Następnie należy użyć [Menedżera pakietów](package-management.md) , takiego jak [Paket](https://fsprojects.github.io/Paket/) lub [NuGet](https://www.nuget.org/) , aby zainstalować pakiet `WindowsAzure.Storage` i informacje referencyjne `WindowsAzure.Storage.dll` w skrypcie przy użyciu dyrektywy `#r`.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-116">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="7b0b7-117">Dodawanie deklaracji przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="7b0b7-117">Add namespace declarations</span></span>

<span data-ttu-id="7b0b7-118">Dodaj następujące instrukcje `open` na początku pliku `files.fsx`:</span><span class="sxs-lookup"><span data-stu-id="7b0b7-118">Add the following `open` statements to the top of the `files.fsx` file:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="7b0b7-119">Uzyskiwanie parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="7b0b7-119">Get your connection string</span></span>

<span data-ttu-id="7b0b7-120">W tym samouczku będą potrzebne parametry połączenia usługi Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-120">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="7b0b7-121">Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz [Konfigurowanie parametrów połączenia magazynu](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="7b0b7-121">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="7b0b7-122">Na potrzeby samouczka wprowadzisz w skrypcie parametry połączenia, takie jak:</span><span class="sxs-lookup"><span data-stu-id="7b0b7-122">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

<span data-ttu-id="7b0b7-123">Nie jest to jednak **zalecane** w przypadku rzeczywistych projektów.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-123">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="7b0b7-124">Klucz konta magazynu jest podobny do hasła głównego konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-124">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="7b0b7-125">Zawsze chroń klucz konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-125">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="7b0b7-126">Nie udostępniaj go innym użytkownikom, nie koduj go trwale ani nie zapisuj w zwykłym pliku tekstowym, do którego mają dostęp inne osoby.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-126">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="7b0b7-127">Możesz ponownie wygenerować klucz za pomocą witryny Azure Portal, jeśli uważasz, że jego zabezpieczenia mogły zostać naruszone.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-127">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="7b0b7-128">W przypadku prawdziwych aplikacji najlepszym sposobem obsługi parametrów połączenia magazynu jest w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-128">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="7b0b7-129">Aby pobrać parametry połączenia z pliku konfiguracji, można to zrobić:</span><span class="sxs-lookup"><span data-stu-id="7b0b7-129">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

<span data-ttu-id="7b0b7-130">Użycie programu Azure Configuration Manager jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-130">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="7b0b7-131">Można również użyć interfejsu API, takiego jak typ `ConfigurationManager` .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-131">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="7b0b7-132">Analizowanie parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="7b0b7-132">Parse the connection string</span></span>

<span data-ttu-id="7b0b7-133">Aby przeanalizować parametry połączenia, użyj:</span><span class="sxs-lookup"><span data-stu-id="7b0b7-133">To parse the connection string, use:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

<span data-ttu-id="7b0b7-134">Spowoduje to zwrócenie `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-134">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-file-service-client"></a><span data-ttu-id="7b0b7-135">Tworzenie klienta usługi plików</span><span class="sxs-lookup"><span data-stu-id="7b0b7-135">Create the File service client</span></span>

<span data-ttu-id="7b0b7-136">Typ `CloudFileClient` umożliwia programistyczne używanie plików przechowywanych w magazynie plików.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-136">The `CloudFileClient` type enables you to programmatically use files stored in File storage.</span></span> <span data-ttu-id="7b0b7-137">Oto jeden ze sposobów tworzenia klienta usługi:</span><span class="sxs-lookup"><span data-stu-id="7b0b7-137">Here's one way to create the service client:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

<span data-ttu-id="7b0b7-138">Teraz możesz przystąpić do pisania kodu, który odczytuje dane z magazynu plików i zapisuje je w nim.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-138">Now you are ready to write code that reads data from and writes data to File storage.</span></span>

## <a name="create-a-file-share"></a><span data-ttu-id="7b0b7-139">Tworzenie udziału plików</span><span class="sxs-lookup"><span data-stu-id="7b0b7-139">Create a file share</span></span>

<span data-ttu-id="7b0b7-140">Ten przykład pokazuje, jak utworzyć udział plików, jeśli jeszcze nie istnieje:</span><span class="sxs-lookup"><span data-stu-id="7b0b7-140">This example shows how to create a file share if it does not already exist:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a><span data-ttu-id="7b0b7-141">Tworzenie katalogu głównego i podkatalogu</span><span class="sxs-lookup"><span data-stu-id="7b0b7-141">Create a root directory and a subdirectory</span></span>

<span data-ttu-id="7b0b7-142">W tym miejscu otrzymujesz katalog główny i uzyskasz podkatalog w katalogu głównym.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-142">Here, you get the root directory and get a sub-directory of the root.</span></span> <span data-ttu-id="7b0b7-143">Należy utworzyć obie, jeśli jeszcze nie istnieją.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-143">You create both if they don't already exist.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a><span data-ttu-id="7b0b7-144">Przekaż tekst jako plik</span><span class="sxs-lookup"><span data-stu-id="7b0b7-144">Upload text as a file</span></span>

<span data-ttu-id="7b0b7-145">Ten przykład pokazuje, jak przekazać tekst jako plik.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-145">This example shows how to upload text as a file.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a><span data-ttu-id="7b0b7-146">Pobierz plik do lokalnej kopii pliku</span><span class="sxs-lookup"><span data-stu-id="7b0b7-146">Download a file to a local copy of the file</span></span>

<span data-ttu-id="7b0b7-147">W tym miejscu pobierasz utworzony plik, dołączając zawartość do pliku lokalnego.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-147">Here you download the file just created, appending the contents to a local file.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a><span data-ttu-id="7b0b7-148">Ustawianie maksymalnego rozmiaru udziału plików</span><span class="sxs-lookup"><span data-stu-id="7b0b7-148">Set the maximum size for a file share</span></span>

<span data-ttu-id="7b0b7-149">W poniższym przykładzie pokazano, jak sprawdzić bieżące użycie udziału oraz jak ustawić limit przydziału w udziale.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-149">The example below shows how to check the current usage for a share and how to set the quota for the share.</span></span> <span data-ttu-id="7b0b7-150">należy wywołać `FetchAttributes`, aby wypełnić `Properties`udziału, i `SetProperties` propagowanie lokalnych zmian do usługi Azure File Storage.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-150">`FetchAttributes` must be called to populate a share's `Properties`, and `SetProperties` to propagate local changes to Azure File storage.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a><span data-ttu-id="7b0b7-151">Generowanie sygnatury dostępu współdzielonego dla pliku lub udziału plików</span><span class="sxs-lookup"><span data-stu-id="7b0b7-151">Generate a shared access signature for a file or file share</span></span>

<span data-ttu-id="7b0b7-152">Można wygenerować sygnaturę dostępu współdzielonego (SAS) dla udziału plików lub dla pojedynczego pliku.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-152">You can generate a shared access signature (SAS) for a file share or for an individual file.</span></span> <span data-ttu-id="7b0b7-153">Można też utworzyć zasady dostępu współdzielonego w udziale plików na potrzeby zarządzania sygnaturami dostępu współdzielonego.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-153">You can also create a shared access policy on a file share to manage shared access signatures.</span></span> <span data-ttu-id="7b0b7-154">Utworzenie zasad dostępu współdzielonego jest zalecane, ponieważ umożliwia cofnięcie sygnatur w przypadku zagrożenia bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-154">Creating a shared access policy is recommended, as it provides a means of revoking the SAS if it should be compromised.</span></span>

<span data-ttu-id="7b0b7-155">W tym miejscu można utworzyć zasady dostępu współdzielonego w udziale, a następnie użyć tych zasad w celu zapewnienia ograniczeń dla SAS dla pliku w udziale.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-155">Here, you create a shared access policy on a share, and then use that policy to provide the constraints for a SAS on a file in the share.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

<span data-ttu-id="7b0b7-156">Aby uzyskać więcej informacji na temat tworzenia i używania sygnatur dostępu współdzielonego, zobacz [Using Shared Access Signatures (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) (Używanie sygnatur dostępu współdzielonego (SAS)) oraz [Create and use a SAS with Blob storage](/azure/storage/storage-dotnet-shared-access-signature-part-2) (Tworzenie i używanie sygnatury dostępu współdzielonego w Magazynie obiektów Blob).</span><span class="sxs-lookup"><span data-stu-id="7b0b7-156">For more information about creating and using shared access signatures, see [Using Shared Access Signatures (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) and [Create and use a SAS with Blob storage](/azure/storage/storage-dotnet-shared-access-signature-part-2).</span></span>

### <a name="copy-files"></a><span data-ttu-id="7b0b7-157">Kopiowanie plików</span><span class="sxs-lookup"><span data-stu-id="7b0b7-157">Copy files</span></span>

<span data-ttu-id="7b0b7-158">Plik można skopiować do innego pliku lub do obiektu BLOB lub do pliku.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-158">You can copy a file to another file or to a blob, or a blob to a file.</span></span> <span data-ttu-id="7b0b7-159">Jeśli kopiujesz obiekt BLOB do pliku lub pliku do obiektu BLOB, *musisz* użyć sygnatury dostępu współdzielonego do uwierzytelnienia obiektu źródłowego, nawet jeśli kopiujesz w ramach tego samego konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-159">If you are copying a blob to a file, or a file to a blob, you *must* use a shared access signature (SAS) to authenticate the source object, even if you are copying within the same storage account.</span></span>

### <a name="copy-a-file-to-another-file"></a><span data-ttu-id="7b0b7-160">Kopiowanie pliku do innego pliku</span><span class="sxs-lookup"><span data-stu-id="7b0b7-160">Copy a file to another file</span></span>

<span data-ttu-id="7b0b7-161">W tym miejscu skopiujesz plik do innego pliku w tym samym udziale.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-161">Here, you copy a file to another file in the same share.</span></span> <span data-ttu-id="7b0b7-162">Ponieważ ta operacja kopiowania jest wykonywana w ramach tego samego konta magazynu, można użyć uwierzytelniania przy użyciu klucza wspólnego.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-162">Because this copy operation copies between files in the same storage account, you can use Shared Key authentication to perform the copy.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a><span data-ttu-id="7b0b7-163">Kopiowanie pliku do obiektu blob</span><span class="sxs-lookup"><span data-stu-id="7b0b7-163">Copy a file to a blob</span></span>

<span data-ttu-id="7b0b7-164">Tutaj utworzysz plik i skopiujesz go do obiektu BLOB w ramach tego samego konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-164">Here, you create a file and copy it to a blob within the same storage account.</span></span> <span data-ttu-id="7b0b7-165">Tworzysz sygnaturę dostępu współdzielonego dla pliku źródłowego, którego usługa używa do uwierzytelniania w pliku źródłowym podczas operacji kopiowania.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-165">You create a SAS for the source file, which the service uses to authenticate access to the source file during the copy operation.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

<span data-ttu-id="7b0b7-166">W ten sam sposób można skopiować obiekt blob do pliku.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-166">You can copy a blob to a file in the same way.</span></span> <span data-ttu-id="7b0b7-167">Jeśli obiekt źródłowy jest obiektem blob, utwórz sygnaturę dostępu współdzielonego w celu uwierzytelniania dostępu do tego obiektu blob podczas operacji kopiowania.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-167">If the source object is a blob, then create a SAS to authenticate access to that blob during the copy operation.</span></span>

## <a name="troubleshooting-file-storage-using-metrics"></a><span data-ttu-id="7b0b7-168">Rozwiązywanie problemów z usługą Magazyn plików przy użyciu metryk</span><span class="sxs-lookup"><span data-stu-id="7b0b7-168">Troubleshooting File storage using metrics</span></span>

<span data-ttu-id="7b0b7-169">Analityka magazynu platformy Azure obsługuje metryki dla usługi File Storage.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-169">Azure Storage Analytics supports metrics for File storage.</span></span> <span data-ttu-id="7b0b7-170">Dane metryk umożliwiają śledzenie żądań i diagnozowanie problemów.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-170">With metrics data, you can trace requests and diagnose issues.</span></span>

<span data-ttu-id="7b0b7-171">Metryki dla usługi File Storage można włączyć w [witrynie Azure Portal](https://portal.azure.com)lub można to zrobić w F# następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7b0b7-171">You can enable metrics for File storage from the [Azure Portal](https://portal.azure.com), or you can do it from F# like this:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a><span data-ttu-id="7b0b7-172">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="7b0b7-172">Next steps</span></span>

<span data-ttu-id="7b0b7-173">Poniższe linki umożliwiają uzyskanie dodatkowych informacji na temat usługi Magazyn plików Azure.</span><span class="sxs-lookup"><span data-stu-id="7b0b7-173">See these links for more information about Azure File storage.</span></span>

### <a name="conceptual-articles-and-videos"></a><span data-ttu-id="7b0b7-174">Artykuły koncepcyjne i filmy</span><span class="sxs-lookup"><span data-stu-id="7b0b7-174">Conceptual articles and videos</span></span>

- <span data-ttu-id="7b0b7-175">[Azure Files Storage: a frictionless cloud SMB file system for Windows and Linux](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/) (Azure File Storage: płynnie działający system plików SMB w chmurze dla systemów Windows i Linux)</span><span class="sxs-lookup"><span data-stu-id="7b0b7-175">[Azure Files Storage: a frictionless cloud SMB file system for Windows and Linux](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)</span></span>
- <span data-ttu-id="7b0b7-176">[How to use Azure File Storage with Linux](/azure/storage/storage-how-to-use-files-linux) (Jak używać usługi Azure File Storage z systemem Linux)</span><span class="sxs-lookup"><span data-stu-id="7b0b7-176">[How to use Azure File Storage with Linux](/azure/storage/storage-how-to-use-files-linux)</span></span>

### <a name="tooling-support-for-file-storage"></a><span data-ttu-id="7b0b7-177">Narzędzia dostępne dla usługi Magazyn plików</span><span class="sxs-lookup"><span data-stu-id="7b0b7-177">Tooling support for File storage</span></span>

- [<span data-ttu-id="7b0b7-178">Używanie programu Azure PowerShell z usługą Azure Storage</span><span class="sxs-lookup"><span data-stu-id="7b0b7-178">Using Azure PowerShell with Azure Storage</span></span>](/azure/storage/storage-powershell-guide-full)
- <span data-ttu-id="7b0b7-179">[How to use AzCopy with Microsoft Azure Storage](/azure/storage/storage-use-azcopy) (Jak używać narzędzia AzCopy z usługą Microsoft Azure Storage)</span><span class="sxs-lookup"><span data-stu-id="7b0b7-179">[How to use AzCopy with Microsoft Azure Storage](/azure/storage/storage-use-azcopy)</span></span>
- [<span data-ttu-id="7b0b7-180">Używanie interfejsu wiersza polecenia platformy Azure z usługą Azure Storage</span><span class="sxs-lookup"><span data-stu-id="7b0b7-180">Using the Azure CLI with Azure Storage</span></span>](/azure/storage/storage-azure-cli#create-and-manage-file-shares)

### <a name="reference"></a><span data-ttu-id="7b0b7-181">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="7b0b7-181">Reference</span></span>

- [<span data-ttu-id="7b0b7-182">Dokumentacja biblioteki klienta usługi Storage dla programu .NET</span><span class="sxs-lookup"><span data-stu-id="7b0b7-182">Storage Client Library for .NET reference</span></span>](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [<span data-ttu-id="7b0b7-183">Dokumentacja interfejsu API REST usługi plików</span><span class="sxs-lookup"><span data-stu-id="7b0b7-183">File Service REST API reference</span></span>](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a><span data-ttu-id="7b0b7-184">Wpisy w blogu</span><span class="sxs-lookup"><span data-stu-id="7b0b7-184">Blog posts</span></span>

- <span data-ttu-id="7b0b7-185">[Azure File storage is now generally available](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/) (Usługa Azure File Storage została udostępniona publicznie)</span><span class="sxs-lookup"><span data-stu-id="7b0b7-185">[Azure File storage is now generally available](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)</span></span>
- <span data-ttu-id="7b0b7-186">[Inside Azure File Storage](https://azure.microsoft.com/blog/inside-azure-file-storage/) (Za kulisami usługi Azure File Storage)</span><span class="sxs-lookup"><span data-stu-id="7b0b7-186">[Inside Azure File Storage](https://azure.microsoft.com/blog/inside-azure-file-storage/)</span></span>
- <span data-ttu-id="7b0b7-187">[Introducing Microsoft Azure File Service](https://docs.microsoft.com/archive/blogs/windowsazurestorage/introducing-microsoft-azure-file-service) (Wprowadzenie do usługi plików platformy Microsoft Azure)</span><span class="sxs-lookup"><span data-stu-id="7b0b7-187">[Introducing Microsoft Azure File Service](https://docs.microsoft.com/archive/blogs/windowsazurestorage/introducing-microsoft-azure-file-service)</span></span>
- <span data-ttu-id="7b0b7-188">[Persisting connections to Microsoft Azure Files](https://docs.microsoft.com/archive/blogs/windowsazurestorage/persisting-connections-to-microsoft-azure-files) (Utrwalanie połączeń z plikami platformy Microsoft Azure)</span><span class="sxs-lookup"><span data-stu-id="7b0b7-188">[Persisting connections to Microsoft Azure Files](https://docs.microsoft.com/archive/blogs/windowsazurestorage/persisting-connections-to-microsoft-azure-files)</span></span>
