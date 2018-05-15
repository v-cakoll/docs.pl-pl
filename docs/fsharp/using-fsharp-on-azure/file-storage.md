---
title: 'Rozpoczynanie pracy z magazynem plików Azure przy użyciu języka F #'
description: Przechowywanie plików danych w chmurze za pomocą magazyn plików Azure i instalowanie udziału plików w chmurze z maszyny wirtualnej platformy Azure (VM) lub z lokalnych aplikacji systemu Windows.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: e772da5f81d2e6827295d0dfe150934a415eb3bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="get-started-with-azure-file-storage-using-f"></a><span data-ttu-id="8e563-103">Rozpoczynanie pracy z magazynem plików Azure przy użyciu języka F #</span><span class="sxs-lookup"><span data-stu-id="8e563-103">Get started with Azure File storage using F#</span></span> #

<span data-ttu-id="8e563-104">Magazyn plików Azure to usługa, która umożliwia udziałów plików w chmurze przy użyciu standardowego [protokołu bloku komunikatów serwera (SMB)](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx).</span><span class="sxs-lookup"><span data-stu-id="8e563-104">Azure File storage is a service that offers file shares in the cloud using the standard [Server Message Block (SMB) Protocol](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx).</span></span> <span data-ttu-id="8e563-105">Obsługiwane są zarówno protokół SMB 2.1 i 3.0 protokołu SMB.</span><span class="sxs-lookup"><span data-stu-id="8e563-105">Both SMB 2.1 and SMB 3.0 are supported.</span></span> <span data-ttu-id="8e563-106">Magazyn plików Azure można migrować starsze aplikacje korzystające z udziałów plików na platformę Azure szybko i bez kosztownych modyfikacji oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="8e563-106">With Azure File storage, you can migrate legacy applications that rely on file shares to Azure quickly and without costly rewrites.</span></span> <span data-ttu-id="8e563-107">Aplikacje działające na maszynach wirtualnych platformy Azure lub usługi w chmurze lub z klientami lokalnymi mogą zainstalować udział plików w chmurze, tak samo jak aplikacja na komputerze instalująca typowy udział SMB.</span><span class="sxs-lookup"><span data-stu-id="8e563-107">Applications running in Azure virtual machines or cloud services or from on-premises clients can mount a file share in the cloud, just as a desktop application mounts a typical SMB share.</span></span> <span data-ttu-id="8e563-108">Dowolna liczba składników aplikacji, a następnie można zainstalować i uzyskać jednocześnie dostęp do udziału plików magazynu.</span><span class="sxs-lookup"><span data-stu-id="8e563-108">Any number of application components can then mount and access the File storage share simultaneously.</span></span>

<span data-ttu-id="8e563-109">Omówienie pojęć dotyczących magazynu plików, zobacz [przewodnik .NET do przechowywania plików](/azure/storage/storage-dotnet-how-to-use-files).</span><span class="sxs-lookup"><span data-stu-id="8e563-109">For a conceptual overview of file storage, please see [the .NET guide for file storage](/azure/storage/storage-dotnet-how-to-use-files).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8e563-110">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="8e563-110">Prerequisites</span></span>

<span data-ttu-id="8e563-111">Aby użyć tego przewodnika, należy najpierw [utworzyć konto magazynu Azure](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="8e563-111">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="8e563-112">Należy również klucz dostępu do magazynu dla tego konta.</span><span class="sxs-lookup"><span data-stu-id="8e563-112">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="8e563-113">Tworzenie skryptu języka F # i rozpocząć F # Interactive</span><span class="sxs-lookup"><span data-stu-id="8e563-113">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="8e563-114">Przykłady w tym artykule można używać w F # aplikacji lub skryptu języka F #.</span><span class="sxs-lookup"><span data-stu-id="8e563-114">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="8e563-115">Aby utworzyć skrypt F #, Utwórz plik o `.fsx` rozszerzenie, na przykład `files.fsx`, w środowiska deweloperskiego F #.</span><span class="sxs-lookup"><span data-stu-id="8e563-115">To create an F# script, create a file with the `.fsx` extension, for example `files.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="8e563-116">Następnie użyj [Menedżera pakietów](package-management.md) takich jak [Paket](https://fsprojects.github.io/Paket/) lub [NuGet](https://www.nuget.org/) do zainstalowania `WindowsAzure.Storage` odwołanie do pakietu i `WindowsAzure.Storage.dll` skryptu za pomocą `#r`dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="8e563-116">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="8e563-117">Dodawanie deklaracji przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="8e563-117">Add namespace declarations</span></span>

<span data-ttu-id="8e563-118">Dodaj następujące `open` instrukcje na początku `files.fsx` pliku:</span><span class="sxs-lookup"><span data-stu-id="8e563-118">Add the following `open` statements to the top of the `files.fsx` file:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="8e563-119">Pobierz ciąg połączenia</span><span class="sxs-lookup"><span data-stu-id="8e563-119">Get your connection string</span></span>

<span data-ttu-id="8e563-120">Parametry połączenia magazynu Azure należy w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="8e563-120">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="8e563-121">Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz [skonfigurować parametry połączenia magazynu](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="8e563-121">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="8e563-122">Samouczek będzie wprowadź parametry połączenia za pomocą skryptu, jak to:</span><span class="sxs-lookup"><span data-stu-id="8e563-122">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

<span data-ttu-id="8e563-123">Jest to jednak **niezalecane** rzeczywiste projektów.</span><span class="sxs-lookup"><span data-stu-id="8e563-123">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="8e563-124">Klucz konta magazynu jest podobny do hasła głównego konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="8e563-124">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="8e563-125">Zawsze starannie Chroń klucz konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="8e563-125">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="8e563-126">Unikaj udostępniaj go innym użytkownikom, kodować je lub zapisać go w pliku jako zwykły tekst, który jest dostępny do innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="8e563-126">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="8e563-127">Można ponownie wygenerować klucz przy użyciu portalu Azure, jeśli uważasz, że mogą zostać naruszone.</span><span class="sxs-lookup"><span data-stu-id="8e563-127">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="8e563-128">Rzeczywiste aplikacje najlepiej przechowywać parametry połączenia magazynu jest w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8e563-128">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="8e563-129">Aby pobrać parametry połączenia w pliku konfiguracji, można to zrobić:</span><span class="sxs-lookup"><span data-stu-id="8e563-129">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

<span data-ttu-id="8e563-130">Przy użyciu programu Azure Configuration Manager jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="8e563-130">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="8e563-131">Można również użyć interfejsu API, takich jak .NET Framework `ConfigurationManager` typu.</span><span class="sxs-lookup"><span data-stu-id="8e563-131">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="8e563-132">Przeanalizować parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="8e563-132">Parse the connection string</span></span>

<span data-ttu-id="8e563-133">Aby przeanalizować parametrów połączenia, należy użyć:</span><span class="sxs-lookup"><span data-stu-id="8e563-133">To parse the connection string, use:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

<span data-ttu-id="8e563-134">Spowoduje to zwrócenie `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="8e563-134">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-file-service-client"></a><span data-ttu-id="8e563-135">Tworzenie klienta usługi plików</span><span class="sxs-lookup"><span data-stu-id="8e563-135">Create the File service client</span></span>

<span data-ttu-id="8e563-136">`CloudFileClient` Typu umożliwia programowane używanie plików przechowywanych w magazynie plików.</span><span class="sxs-lookup"><span data-stu-id="8e563-136">The `CloudFileClient` type enables you to programmatically use files stored in File storage.</span></span> <span data-ttu-id="8e563-137">Oto jeden ze sposobów tworzenia klienta usługi:</span><span class="sxs-lookup"><span data-stu-id="8e563-137">Here's one way to create the service client:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

<span data-ttu-id="8e563-138">Teraz można przystąpić do pisania kodu, która odczytuje i zapisuje dane do magazynu plików.</span><span class="sxs-lookup"><span data-stu-id="8e563-138">Now you are ready to write code that reads data from and writes data to File storage.</span></span>

## <a name="create-a-file-share"></a><span data-ttu-id="8e563-139">Tworzenie udziału plików</span><span class="sxs-lookup"><span data-stu-id="8e563-139">Create a file share</span></span>

<span data-ttu-id="8e563-140">W tym przykładzie pokazano, jak utworzyć udział plików, jeśli jeszcze nie istnieje:</span><span class="sxs-lookup"><span data-stu-id="8e563-140">This example shows how to create a file share if it does not already exist:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a><span data-ttu-id="8e563-141">Utwórz katalog główny i podkatalogu</span><span class="sxs-lookup"><span data-stu-id="8e563-141">Create a root directory and a subdirectory</span></span>

<span data-ttu-id="8e563-142">W tym miejscu możesz uzyskać katalogu głównego i uzyskać podkatalogiem katalogu głównego.</span><span class="sxs-lookup"><span data-stu-id="8e563-142">Here, you get the root directory and get a sub-directory of the root.</span></span> <span data-ttu-id="8e563-143">Możesz utworzyć obie Jeśli jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="8e563-143">You create both if they don't already exist.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a><span data-ttu-id="8e563-144">Przekaż tekst w formacie</span><span class="sxs-lookup"><span data-stu-id="8e563-144">Upload text as a file</span></span>

<span data-ttu-id="8e563-145">Ten przykład przedstawia sposób przekazywania tekstu jako plik.</span><span class="sxs-lookup"><span data-stu-id="8e563-145">This example shows how to upload text as a file.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a><span data-ttu-id="8e563-146">Pobierz plik do lokalnej kopii pliku</span><span class="sxs-lookup"><span data-stu-id="8e563-146">Download a file to a local copy of the file</span></span>

<span data-ttu-id="8e563-147">W tym miejscu Pobierz plik właśnie utworzony dołączania zawartości do pliku lokalnego.</span><span class="sxs-lookup"><span data-stu-id="8e563-147">Here you download the file just created, appending the contents to a local file.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a><span data-ttu-id="8e563-148">Ustawianie maksymalnego rozmiaru udziału plików</span><span class="sxs-lookup"><span data-stu-id="8e563-148">Set the maximum size for a file share</span></span>

<span data-ttu-id="8e563-149">W poniższym przykładzie pokazano, jak sprawdzić bieżące użycie udziału oraz jak ustawić limit przydziału dla udziału.</span><span class="sxs-lookup"><span data-stu-id="8e563-149">The example below shows how to check the current usage for a share and how to set the quota for the share.</span></span> <span data-ttu-id="8e563-150">`FetchAttributes` musi zostać wywołana, aby wypełnić udziału `Properties`, i `SetProperties` propagowanie zmian lokalnych do usługi Magazyn plików Azure.</span><span class="sxs-lookup"><span data-stu-id="8e563-150">`FetchAttributes` must be called to populate a share's `Properties`, and `SetProperties` to propagate local changes to Azure File storage.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a><span data-ttu-id="8e563-151">Generowanie sygnatury dostępu współdzielonego dla pliku lub udziału plików</span><span class="sxs-lookup"><span data-stu-id="8e563-151">Generate a shared access signature for a file or file share</span></span>

<span data-ttu-id="8e563-152">Możesz wygenerować sygnaturę dostępu współdzielonego (SAS) dla udziału plików lub dla pojedynczego pliku.</span><span class="sxs-lookup"><span data-stu-id="8e563-152">You can generate a shared access signature (SAS) for a file share or for an individual file.</span></span> <span data-ttu-id="8e563-153">Można również utworzyć zasady dostępu współdzielonego w udziale plików do zarządzania sygnaturami dostępu współdzielonego.</span><span class="sxs-lookup"><span data-stu-id="8e563-153">You can also create a shared access policy on a file share to manage shared access signatures.</span></span> <span data-ttu-id="8e563-154">Tworzenie zasad dostępu współdzielonego jest zalecane, ponieważ umożliwia cofnięcie Sygnatur w przypadku powinien być naruszenia zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="8e563-154">Creating a shared access policy is recommended, as it provides a means of revoking the SAS if it should be compromised.</span></span>

<span data-ttu-id="8e563-155">W tym miejscu Utwórz wspólne zasady w udziale dostępu, a następnie użyj tego zasad nakładane są ograniczenia na sygnatury dostępu Współdzielonego w pliku w udziale.</span><span class="sxs-lookup"><span data-stu-id="8e563-155">Here, you create a shared access policy on a share, and then use that policy to provide the constraints for a SAS on a file in the share.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

<span data-ttu-id="8e563-156">Aby uzyskać więcej informacji na temat tworzenia i używania sygnatur dostępu współdzielonego, zobacz [za pomocą sygnatur dostępu do udostępnionych (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) i [tworzenie i używanie sygnatury dostępu Współdzielonego z magazynem obiektów Blob](/azure/storage/storage-dotnet-shared-access-signature-part-2).</span><span class="sxs-lookup"><span data-stu-id="8e563-156">For more information about creating and using shared access signatures, see [Using Shared Access Signatures (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) and [Create and use a SAS with Blob storage](/azure/storage/storage-dotnet-shared-access-signature-part-2).</span></span>

### <a name="copy-files"></a><span data-ttu-id="8e563-157">Skopiuj pliki</span><span class="sxs-lookup"><span data-stu-id="8e563-157">Copy files</span></span>

<span data-ttu-id="8e563-158">Plik można skopiować do innego pliku, lub do obiektu blob oraz obiekty blob do pliku.</span><span class="sxs-lookup"><span data-stu-id="8e563-158">You can copy a file to another file or to a blob, or a blob to a file.</span></span> <span data-ttu-id="8e563-159">Jeśli kopiujesz obiektu blob do pliku lub pliku do obiektu blob, możesz *musi* Użyj sygnatury dostępu współdzielonego (SAS) do uwierzytelniania obiektu źródłowego, nawet jeśli kopiujesz w ramach tego samego konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="8e563-159">If you are copying a blob to a file, or a file to a blob, you *must* use a shared access signature (SAS) to authenticate the source object, even if you are copying within the same storage account.</span></span>

### <a name="copy-a-file-to-another-file"></a><span data-ttu-id="8e563-160">Kopiowanie pliku do innego pliku</span><span class="sxs-lookup"><span data-stu-id="8e563-160">Copy a file to another file</span></span>

<span data-ttu-id="8e563-161">W tym miejscu można skopiować pliku do innego pliku w tym samym udziale.</span><span class="sxs-lookup"><span data-stu-id="8e563-161">Here, you copy a file to another file in the same share.</span></span> <span data-ttu-id="8e563-162">Ponieważ ta operacja kopiowania kopiuje między plikami w tym samym koncie magazynu, można użyć uwierzytelniania klucza wspólnego do wykonania kopii.</span><span class="sxs-lookup"><span data-stu-id="8e563-162">Because this copy operation copies between files in the same storage account, you can use Shared Key authentication to perform the copy.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a><span data-ttu-id="8e563-163">Kopiowanie pliku do obiektu blob</span><span class="sxs-lookup"><span data-stu-id="8e563-163">Copy a file to a blob</span></span>

<span data-ttu-id="8e563-164">W tym miejscu Utwórz plik i skopiuj go do obiektu blob w ramach tego samego konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="8e563-164">Here, you create a file and copy it to a blob within the same storage account.</span></span> <span data-ttu-id="8e563-165">Możesz utworzyć sygnatury dostępu Współdzielonego dla pliku źródłowego, który usługa używa do uwierzytelniania dostępu do pliku źródłowego podczas operacji kopiowania.</span><span class="sxs-lookup"><span data-stu-id="8e563-165">You create a SAS for the source file, which the service uses to authenticate access to the source file during the copy operation.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

<span data-ttu-id="8e563-166">W ten sam sposób można skopiować obiektu blob do pliku.</span><span class="sxs-lookup"><span data-stu-id="8e563-166">You can copy a blob to a file in the same way.</span></span> <span data-ttu-id="8e563-167">Jeśli obiekt źródłowy jest obiektem blob, następnie utwórz sygnaturę dostępu Współdzielonego w celu uwierzytelniania dostępu do tego obiektu blob podczas operacji kopiowania.</span><span class="sxs-lookup"><span data-stu-id="8e563-167">If the source object is a blob, then create a SAS to authenticate access to that blob during the copy operation.</span></span>

## <a name="troubleshooting-file-storage-using-metrics"></a><span data-ttu-id="8e563-168">Rozwiązywanie problemów z magazynem plików przy użyciu metryk</span><span class="sxs-lookup"><span data-stu-id="8e563-168">Troubleshooting File storage using metrics</span></span>

<span data-ttu-id="8e563-169">Analizy usługi Azure Storage obsługuje metryki dla usługi Magazyn plików.</span><span class="sxs-lookup"><span data-stu-id="8e563-169">Azure Storage Analytics supports metrics for File storage.</span></span> <span data-ttu-id="8e563-170">Dane metryk możesz Śledzenie żądań i diagnozowanie problemów.</span><span class="sxs-lookup"><span data-stu-id="8e563-170">With metrics data, you can trace requests and diagnose issues.</span></span>

<span data-ttu-id="8e563-171">Można włączyć metryki dla usługi Magazyn plików [Azure Portal](https://portal.azure.com), lub czy z F # następująco:</span><span class="sxs-lookup"><span data-stu-id="8e563-171">You can enable metrics for File storage from the [Azure Portal](https://portal.azure.com), or you can do it from F# like this:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a><span data-ttu-id="8e563-172">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="8e563-172">Next steps</span></span>

<span data-ttu-id="8e563-173">Zobacz następujące łącza, aby uzyskać więcej informacji na temat usługi Magazyn plików Azure.</span><span class="sxs-lookup"><span data-stu-id="8e563-173">See these links for more information about Azure File storage.</span></span>

### <a name="conceptual-articles-and-videos"></a><span data-ttu-id="8e563-174">Artykuły koncepcyjne i filmy</span><span class="sxs-lookup"><span data-stu-id="8e563-174">Conceptual articles and videos</span></span>

- [<span data-ttu-id="8e563-175">Azure File Storage: frictionless cloud SMB systemu plików dla systemu Windows i Linux</span><span class="sxs-lookup"><span data-stu-id="8e563-175">Azure Files Storage: a frictionless cloud SMB file system for Windows and Linux</span></span>](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [<span data-ttu-id="8e563-176">Jak używać magazynu plików Azure z systemem Linux</span><span class="sxs-lookup"><span data-stu-id="8e563-176">How to use Azure File Storage with Linux</span></span>](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a><span data-ttu-id="8e563-177">Narzędzia dostępne do przechowywania plików</span><span class="sxs-lookup"><span data-stu-id="8e563-177">Tooling support for File storage</span></span>

- [<span data-ttu-id="8e563-178">Używanie programu Azure PowerShell z usługą Azure Storage</span><span class="sxs-lookup"><span data-stu-id="8e563-178">Using Azure PowerShell with Azure Storage</span></span>](/azure/storage/storage-powershell-guide-full)
- [<span data-ttu-id="8e563-179">Jak używać narzędzia AzCopy z usługi Magazyn Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="8e563-179">How to use AzCopy with Microsoft Azure Storage</span></span>](/azure/storage/storage-use-azcopy)
- [<span data-ttu-id="8e563-180">Przy użyciu interfejsu wiersza polecenia platformy Azure z usługą Azure Storage</span><span class="sxs-lookup"><span data-stu-id="8e563-180">Using the Azure CLI with Azure Storage</span></span>](/azure/storage/storage-azure-cli#create-and-manage-file-shares)

### <a name="reference"></a><span data-ttu-id="8e563-181">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="8e563-181">Reference</span></span>

- [<span data-ttu-id="8e563-182">Biblioteka klienta usługi Storage dla platformy .NET odwołania</span><span class="sxs-lookup"><span data-stu-id="8e563-182">Storage Client Library for .NET reference</span></span>](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [<span data-ttu-id="8e563-183">Dokumentacja interfejsu API REST usługi plików</span><span class="sxs-lookup"><span data-stu-id="8e563-183">File Service REST API reference</span></span>](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a><span data-ttu-id="8e563-184">Wpisy na blogu</span><span class="sxs-lookup"><span data-stu-id="8e563-184">Blog posts</span></span>

- [<span data-ttu-id="8e563-185">Magazyn plików Azure jest ogólnie dostępna teraz</span><span class="sxs-lookup"><span data-stu-id="8e563-185">Azure File storage is now generally available</span></span>](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [<span data-ttu-id="8e563-186">Inside Azure File Storage</span><span class="sxs-lookup"><span data-stu-id="8e563-186">Inside Azure File Storage</span></span>](https://azure.microsoft.com/blog/inside-azure-file-storage/) 
- [<span data-ttu-id="8e563-187">Wprowadzenie do usługi Microsoft Azure pliku</span><span class="sxs-lookup"><span data-stu-id="8e563-187">Introducing Microsoft Azure File Service</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/12/introducing-microsoft-azure-file-service/)
- [<span data-ttu-id="8e563-188">Utrwalanie połączeń pliki programu Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="8e563-188">Persisting connections to Microsoft Azure Files</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/26/persisting-connections-to-microsoft-azure-files/)
