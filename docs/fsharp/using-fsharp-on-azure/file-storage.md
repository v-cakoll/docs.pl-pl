---
title: Rozpoczynanie pracy z usługą Azure File storage przy użyciu języka F#
description: Store danych plików w chmurze za pomocą usługi Azure File storage i instalowanie udziału plików w chmurze z maszyny wirtualnej (VM) platformy Azure lub z aplikacji w środowisku lokalnym systemem Windows.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: e772da5f81d2e6827295d0dfe150934a415eb3bb
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "33569346"
---
# <a name="get-started-with-azure-file-storage-using-f"></a><span data-ttu-id="e78b6-103">Rozpoczynanie pracy z usługą Azure File storage przy użyciu języka F#</span><span class="sxs-lookup"><span data-stu-id="e78b6-103">Get started with Azure File storage using F#</span></span> #

<span data-ttu-id="e78b6-104">Usługa Azure File storage to usługa, która oferuje udziały plików w chmurze przy użyciu standardowych [protokołu bloku komunikatów serwera (SMB)](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx).</span><span class="sxs-lookup"><span data-stu-id="e78b6-104">Azure File storage is a service that offers file shares in the cloud using the standard [Server Message Block (SMB) Protocol](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx).</span></span> <span data-ttu-id="e78b6-105">Obsługiwane są zarówno protokół SMB 2.1, jak i protokołu SMB 3.0.</span><span class="sxs-lookup"><span data-stu-id="e78b6-105">Both SMB 2.1 and SMB 3.0 are supported.</span></span> <span data-ttu-id="e78b6-106">Za pomocą usługi Azure File storage można migrować starsze aplikacje korzystające z udziałów plików na platformę Azure, szybko i bez kosztownych modyfikacji oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="e78b6-106">With Azure File storage, you can migrate legacy applications that rely on file shares to Azure quickly and without costly rewrites.</span></span> <span data-ttu-id="e78b6-107">Aplikacje działające w usłudze Azure virtual machines lub cloud services lub z klientów lokalnych można zainstalować udział plików w chmurze, tak samo, jak aplikacja na komputerze instalująca typowy udział SMB.</span><span class="sxs-lookup"><span data-stu-id="e78b6-107">Applications running in Azure virtual machines or cloud services or from on-premises clients can mount a file share in the cloud, just as a desktop application mounts a typical SMB share.</span></span> <span data-ttu-id="e78b6-108">Dowolna liczba składników aplikacji, a następnie można zainstalować i jednocześnie dostęp do udziału pliku magazynu.</span><span class="sxs-lookup"><span data-stu-id="e78b6-108">Any number of application components can then mount and access the File storage share simultaneously.</span></span>

<span data-ttu-id="e78b6-109">Omówienie usługi file storage można znaleźć [przewodnik platformy .NET dla usługi file storage](/azure/storage/storage-dotnet-how-to-use-files).</span><span class="sxs-lookup"><span data-stu-id="e78b6-109">For a conceptual overview of file storage, please see [the .NET guide for file storage](/azure/storage/storage-dotnet-how-to-use-files).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e78b6-110">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="e78b6-110">Prerequisites</span></span>

<span data-ttu-id="e78b6-111">Aby użyć tego przewodnika, należy najpierw [Tworzenie konta usługi Azure storage](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="e78b6-111">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="e78b6-112">Należy także klucz dostępu do magazynu dla tego konta.</span><span class="sxs-lookup"><span data-stu-id="e78b6-112">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="e78b6-113">Utwórz skrypt F# i Rozpocznij języka F# Interactive</span><span class="sxs-lookup"><span data-stu-id="e78b6-113">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="e78b6-114">Przykłady w tym artykule może służyć w aplikacji F# lub skryptu F#.</span><span class="sxs-lookup"><span data-stu-id="e78b6-114">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="e78b6-115">Aby utworzyć skrypt F#, Utwórz plik o `.fsx` rozszerzenia, na przykład `files.fsx`, w środowisku projektowym F#.</span><span class="sxs-lookup"><span data-stu-id="e78b6-115">To create an F# script, create a file with the `.fsx` extension, for example `files.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="e78b6-116">Następnie użyj [Menedżera pakietów](package-management.md) takich jak [Paket](https://fsprojects.github.io/Paket/) lub [NuGet](https://www.nuget.org/) zainstalował `WindowsAzure.Storage` pakietów i odwołań `WindowsAzure.Storage.dll` w skrypcie za pomocą `#r`dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="e78b6-116">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="e78b6-117">Dodawanie deklaracji przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="e78b6-117">Add namespace declarations</span></span>

<span data-ttu-id="e78b6-118">Dodaj następujący kod `open` instrukcji na górze `files.fsx` pliku:</span><span class="sxs-lookup"><span data-stu-id="e78b6-118">Add the following `open` statements to the top of the `files.fsx` file:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="e78b6-119">Pobieranie parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="e78b6-119">Get your connection string</span></span>

<span data-ttu-id="e78b6-120">Na potrzeby tego samouczka konieczne będzie parametrów połączenia usługi Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="e78b6-120">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="e78b6-121">Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz [skonfigurować parametry połączenia magazynu](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="e78b6-121">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="e78b6-122">Samouczek wprowadzisz parametrów połączenia w skrypcie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e78b6-122">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

<span data-ttu-id="e78b6-123">Jest to jednak **niezalecane** rzeczywiste projektów.</span><span class="sxs-lookup"><span data-stu-id="e78b6-123">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="e78b6-124">Klucz konta magazynu jest podobny do hasła głównego konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="e78b6-124">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="e78b6-125">Zawsze starannie Chroń klucz konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="e78b6-125">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="e78b6-126">Należy unikać, ich dystrybucję w innym użytkownikom, kodować je lub zapisanie go w pliku tekstowego, który jest dostępny dla innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="e78b6-126">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="e78b6-127">Można ponownie wygenerować klucz za pośrednictwem witryny Azure Portal, jeśli uważasz, że mogą zostać przejęte.</span><span class="sxs-lookup"><span data-stu-id="e78b6-127">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="e78b6-128">Rzeczywiste aplikacje najlepiej przechowywać parametry połączenia magazynu jest w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e78b6-128">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="e78b6-129">Aby pobrać parametry połączenia z pliku konfiguracji, można to zrobić:</span><span class="sxs-lookup"><span data-stu-id="e78b6-129">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

<span data-ttu-id="e78b6-130">Użycie programu Azure Configuration Manager jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="e78b6-130">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="e78b6-131">Można również użyć interfejsu API, takich jak .NET Framework `ConfigurationManager` typu.</span><span class="sxs-lookup"><span data-stu-id="e78b6-131">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="e78b6-132">Przeanalizować parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="e78b6-132">Parse the connection string</span></span>

<span data-ttu-id="e78b6-133">Aby przeanalizować parametrów połączenia, należy użyć:</span><span class="sxs-lookup"><span data-stu-id="e78b6-133">To parse the connection string, use:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

<span data-ttu-id="e78b6-134">Spowoduje to zwrócenie `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="e78b6-134">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-file-service-client"></a><span data-ttu-id="e78b6-135">Tworzenie klienta usługi plików</span><span class="sxs-lookup"><span data-stu-id="e78b6-135">Create the File service client</span></span>

<span data-ttu-id="e78b6-136">`CloudFileClient` Typu umożliwia programowe używanie plików przechowywanych w usłudze File storage.</span><span class="sxs-lookup"><span data-stu-id="e78b6-136">The `CloudFileClient` type enables you to programmatically use files stored in File storage.</span></span> <span data-ttu-id="e78b6-137">Oto jeden ze sposobów tworzenia klienta usługi:</span><span class="sxs-lookup"><span data-stu-id="e78b6-137">Here's one way to create the service client:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

<span data-ttu-id="e78b6-138">Teraz możesz przystąpić do pisania kodu, który odczytuje dane z i zapisuje dane do magazynu plików.</span><span class="sxs-lookup"><span data-stu-id="e78b6-138">Now you are ready to write code that reads data from and writes data to File storage.</span></span>

## <a name="create-a-file-share"></a><span data-ttu-id="e78b6-139">Utwórz udział plików</span><span class="sxs-lookup"><span data-stu-id="e78b6-139">Create a file share</span></span>

<span data-ttu-id="e78b6-140">W tym przykładzie pokazano, jak utworzyć udział plików, jeśli jeszcze nie istnieje:</span><span class="sxs-lookup"><span data-stu-id="e78b6-140">This example shows how to create a file share if it does not already exist:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a><span data-ttu-id="e78b6-141">Utwórz katalog główny i to podkatalog</span><span class="sxs-lookup"><span data-stu-id="e78b6-141">Create a root directory and a subdirectory</span></span>

<span data-ttu-id="e78b6-142">W tym miejscu otrzymasz katalog główny i pobrać podrzędnych katalogu głównego.</span><span class="sxs-lookup"><span data-stu-id="e78b6-142">Here, you get the root directory and get a sub-directory of the root.</span></span> <span data-ttu-id="e78b6-143">Możesz utworzyć obie Jeśli jeszcze nie istnieją.</span><span class="sxs-lookup"><span data-stu-id="e78b6-143">You create both if they don't already exist.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a><span data-ttu-id="e78b6-144">Prześlij tekst jako plik</span><span class="sxs-lookup"><span data-stu-id="e78b6-144">Upload text as a file</span></span>

<span data-ttu-id="e78b6-145">Ten przykład przedstawia sposób przekazywania tekst w formacie.</span><span class="sxs-lookup"><span data-stu-id="e78b6-145">This example shows how to upload text as a file.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a><span data-ttu-id="e78b6-146">Pobierz plik w lokalnej kopii pliku</span><span class="sxs-lookup"><span data-stu-id="e78b6-146">Download a file to a local copy of the file</span></span>

<span data-ttu-id="e78b6-147">Tutaj możesz pobrać plik, który został właśnie utworzony, dołącza zawartość do pliku lokalnego.</span><span class="sxs-lookup"><span data-stu-id="e78b6-147">Here you download the file just created, appending the contents to a local file.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a><span data-ttu-id="e78b6-148">Ustaw maksymalny rozmiar udziału plików</span><span class="sxs-lookup"><span data-stu-id="e78b6-148">Set the maximum size for a file share</span></span>

<span data-ttu-id="e78b6-149">W poniższym przykładzie pokazano, jak sprawdzić bieżące użycie udziału oraz jak ustawić limit przydziału dla udziału.</span><span class="sxs-lookup"><span data-stu-id="e78b6-149">The example below shows how to check the current usage for a share and how to set the quota for the share.</span></span> <span data-ttu-id="e78b6-150">`FetchAttributes` musi zostać wywołana w celu wypełnienia udziału `Properties`, i `SetProperties` propagowanie zmian lokalnych do usługi Azure File storage.</span><span class="sxs-lookup"><span data-stu-id="e78b6-150">`FetchAttributes` must be called to populate a share's `Properties`, and `SetProperties` to propagate local changes to Azure File storage.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a><span data-ttu-id="e78b6-151">Generowanie sygnatury dostępu współdzielonego dla pliku lub udziału plików</span><span class="sxs-lookup"><span data-stu-id="e78b6-151">Generate a shared access signature for a file or file share</span></span>

<span data-ttu-id="e78b6-152">Można wygenerować sygnatury dostępu współdzielonego (SAS) dla udziału plików lub dla pojedynczego pliku.</span><span class="sxs-lookup"><span data-stu-id="e78b6-152">You can generate a shared access signature (SAS) for a file share or for an individual file.</span></span> <span data-ttu-id="e78b6-153">Można również utworzyć zasady dostępu współdzielonego w udziale plików, aby zarządzać sygnatur dostępu współdzielonego.</span><span class="sxs-lookup"><span data-stu-id="e78b6-153">You can also create a shared access policy on a file share to manage shared access signatures.</span></span> <span data-ttu-id="e78b6-154">Tworzenie zasad dostępu współdzielonego jest zalecane, ponieważ umożliwia cofnięcie Sygnatur w przypadku powinien być naruszenia zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="e78b6-154">Creating a shared access policy is recommended, as it provides a means of revoking the SAS if it should be compromised.</span></span>

<span data-ttu-id="e78b6-155">W tym miejscu tworzysz wspólny dostęp do zasad w udziale, a następnie użyć tych zasad nakładane są ograniczenia na sygnatury dostępu Współdzielonego dla pliku w udziale.</span><span class="sxs-lookup"><span data-stu-id="e78b6-155">Here, you create a shared access policy on a share, and then use that policy to provide the constraints for a SAS on a file in the share.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

<span data-ttu-id="e78b6-156">Aby uzyskać więcej informacji na temat tworzenia i używania sygnatur dostępu współdzielonego, zobacz [za pomocą sygnatur dostępu udostępnionego (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) i [tworzenia i używania sygnatur dostępu Współdzielonego z usługą Blob storage](/azure/storage/storage-dotnet-shared-access-signature-part-2).</span><span class="sxs-lookup"><span data-stu-id="e78b6-156">For more information about creating and using shared access signatures, see [Using Shared Access Signatures (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) and [Create and use a SAS with Blob storage](/azure/storage/storage-dotnet-shared-access-signature-part-2).</span></span>

### <a name="copy-files"></a><span data-ttu-id="e78b6-157">Kopiowanie plików</span><span class="sxs-lookup"><span data-stu-id="e78b6-157">Copy files</span></span>

<span data-ttu-id="e78b6-158">Można skopiować pliku do innego pliku lub do obiektu blob oraz obiekty blob do pliku.</span><span class="sxs-lookup"><span data-stu-id="e78b6-158">You can copy a file to another file or to a blob, or a blob to a file.</span></span> <span data-ttu-id="e78b6-159">Podczas kopiowania obiektu blob do pliku lub pliku do obiektu blob, możesz *musi* używają sygnatury dostępu współdzielonego (SAS) do uwierzytelniania obiektu źródłowego, nawet wtedy, gdy są kopiowane w ramach tego samego konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="e78b6-159">If you are copying a blob to a file, or a file to a blob, you *must* use a shared access signature (SAS) to authenticate the source object, even if you are copying within the same storage account.</span></span>

### <a name="copy-a-file-to-another-file"></a><span data-ttu-id="e78b6-160">Kopiowanie pliku do innego pliku</span><span class="sxs-lookup"><span data-stu-id="e78b6-160">Copy a file to another file</span></span>

<span data-ttu-id="e78b6-161">W tym miejscu można skopiować pliku do innego pliku w tym samym udziale.</span><span class="sxs-lookup"><span data-stu-id="e78b6-161">Here, you copy a file to another file in the same share.</span></span> <span data-ttu-id="e78b6-162">Ponieważ ta operacja kopiowania kopiuje między plikami na tym samym koncie magazynu, można użyć uwierzytelniania klucza wspólnego, do wykonania kopii.</span><span class="sxs-lookup"><span data-stu-id="e78b6-162">Because this copy operation copies between files in the same storage account, you can use Shared Key authentication to perform the copy.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a><span data-ttu-id="e78b6-163">Kopiowanie pliku do obiektu blob</span><span class="sxs-lookup"><span data-stu-id="e78b6-163">Copy a file to a blob</span></span>

<span data-ttu-id="e78b6-164">W tym miejscu należy utworzyć plik i skopiuj go do obiektu blob w ramach tego samego konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="e78b6-164">Here, you create a file and copy it to a blob within the same storage account.</span></span> <span data-ttu-id="e78b6-165">Możesz utworzyć sygnaturę dostępu Współdzielonego dla pliku źródłowego, w której usługa uwierzytelniania dostępu do pliku źródłowego podczas operacji kopiowania.</span><span class="sxs-lookup"><span data-stu-id="e78b6-165">You create a SAS for the source file, which the service uses to authenticate access to the source file during the copy operation.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

<span data-ttu-id="e78b6-166">W ten sam sposób, można skopiować obiektu blob do pliku.</span><span class="sxs-lookup"><span data-stu-id="e78b6-166">You can copy a blob to a file in the same way.</span></span> <span data-ttu-id="e78b6-167">Jeśli obiekt źródłowy jest obiektem blob, Utwórz sygnaturę dostępu Współdzielonego w celu uwierzytelnienia dostępu do tego obiektu blob podczas operacji kopiowania.</span><span class="sxs-lookup"><span data-stu-id="e78b6-167">If the source object is a blob, then create a SAS to authenticate access to that blob during the copy operation.</span></span>

## <a name="troubleshooting-file-storage-using-metrics"></a><span data-ttu-id="e78b6-168">Rozwiązywanie problemów z magazynem plików przy użyciu metryk</span><span class="sxs-lookup"><span data-stu-id="e78b6-168">Troubleshooting File storage using metrics</span></span>

<span data-ttu-id="e78b6-169">Analizy usługi Azure Storage obsługuje metryki dla usługi File storage.</span><span class="sxs-lookup"><span data-stu-id="e78b6-169">Azure Storage Analytics supports metrics for File storage.</span></span> <span data-ttu-id="e78b6-170">Dane metryk można Śledzenie żądań i diagnozowanie problemów.</span><span class="sxs-lookup"><span data-stu-id="e78b6-170">With metrics data, you can trace requests and diagnose issues.</span></span>

<span data-ttu-id="e78b6-171">Możesz włączyć metryki dla usługi File storage z [witryny Azure Portal](https://portal.azure.com), lub możesz to zrobić z F# następująco:</span><span class="sxs-lookup"><span data-stu-id="e78b6-171">You can enable metrics for File storage from the [Azure Portal](https://portal.azure.com), or you can do it from F# like this:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a><span data-ttu-id="e78b6-172">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="e78b6-172">Next steps</span></span>

<span data-ttu-id="e78b6-173">Zobacz te linki, aby uzyskać więcej informacji na temat usługi Azure File storage.</span><span class="sxs-lookup"><span data-stu-id="e78b6-173">See these links for more information about Azure File storage.</span></span>

### <a name="conceptual-articles-and-videos"></a><span data-ttu-id="e78b6-174">Artykuły koncepcyjne i filmy</span><span class="sxs-lookup"><span data-stu-id="e78b6-174">Conceptual articles and videos</span></span>

- [<span data-ttu-id="e78b6-175">Usługa Azure Files Storage: frictionless cloud SMB file system for plików Windows i Linux</span><span class="sxs-lookup"><span data-stu-id="e78b6-175">Azure Files Storage: a frictionless cloud SMB file system for Windows and Linux</span></span>](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [<span data-ttu-id="e78b6-176">Jak używać usługi Azure File Storage z systemem Linux</span><span class="sxs-lookup"><span data-stu-id="e78b6-176">How to use Azure File Storage with Linux</span></span>](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a><span data-ttu-id="e78b6-177">Narzędzia do obsługi dla usługi File storage</span><span class="sxs-lookup"><span data-stu-id="e78b6-177">Tooling support for File storage</span></span>

- [<span data-ttu-id="e78b6-178">Używanie programu Azure PowerShell z usługą Azure Storage</span><span class="sxs-lookup"><span data-stu-id="e78b6-178">Using Azure PowerShell with Azure Storage</span></span>](/azure/storage/storage-powershell-guide-full)
- [<span data-ttu-id="e78b6-179">Jak używać narzędzia AzCopy z usługą Microsoft Azure Storage</span><span class="sxs-lookup"><span data-stu-id="e78b6-179">How to use AzCopy with Microsoft Azure Storage</span></span>](/azure/storage/storage-use-azcopy)
- [<span data-ttu-id="e78b6-180">Przy użyciu wiersza polecenia platformy Azure z usługą Azure Storage</span><span class="sxs-lookup"><span data-stu-id="e78b6-180">Using the Azure CLI with Azure Storage</span></span>](/azure/storage/storage-azure-cli#create-and-manage-file-shares)

### <a name="reference"></a><span data-ttu-id="e78b6-181">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="e78b6-181">Reference</span></span>

- [<span data-ttu-id="e78b6-182">Biblioteka klienta usługi Storage dla platformy .NET odwołania</span><span class="sxs-lookup"><span data-stu-id="e78b6-182">Storage Client Library for .NET reference</span></span>](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [<span data-ttu-id="e78b6-183">Dokumentacja interfejsu API REST usługi plików</span><span class="sxs-lookup"><span data-stu-id="e78b6-183">File Service REST API reference</span></span>](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a><span data-ttu-id="e78b6-184">Wpisy w blogu</span><span class="sxs-lookup"><span data-stu-id="e78b6-184">Blog posts</span></span>

- [<span data-ttu-id="e78b6-185">Usługa Azure File storage jest teraz ogólnie dostępna</span><span class="sxs-lookup"><span data-stu-id="e78b6-185">Azure File storage is now generally available</span></span>](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [<span data-ttu-id="e78b6-186">Inside Azure File Storage</span><span class="sxs-lookup"><span data-stu-id="e78b6-186">Inside Azure File Storage</span></span>](https://azure.microsoft.com/blog/inside-azure-file-storage/) 
- [<span data-ttu-id="e78b6-187">Wprowadzenie do usługi Microsoft Azure File Service</span><span class="sxs-lookup"><span data-stu-id="e78b6-187">Introducing Microsoft Azure File Service</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/12/introducing-microsoft-azure-file-service/)
- [<span data-ttu-id="e78b6-188">Persisting Connections to Microsoft Azure Files połączeń</span><span class="sxs-lookup"><span data-stu-id="e78b6-188">Persisting connections to Microsoft Azure Files</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/26/persisting-connections-to-microsoft-azure-files/)
