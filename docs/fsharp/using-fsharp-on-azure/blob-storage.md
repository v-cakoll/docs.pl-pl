---
title: 'Wprowadzenie do usługi Azure Blob storage przy użyciu języka F #'
description: Store danych bez struktury w chmurze za pomocą usługi Azure Blob storage.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: ea9dc334ec9c2bcd4a80cc501d4b6634da5f64e4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43734476"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a><span data-ttu-id="56acb-103">Wprowadzenie do usługi Azure Blob storage przy użyciu języka F #</span><span class="sxs-lookup"><span data-stu-id="56acb-103">Get started with Azure Blob storage using F#</span></span> #

<span data-ttu-id="56acb-104">Usługa Azure Blob storage to usługa, która przechowuje dane niestrukturalne w chmurze w postaci obiektów blob.</span><span class="sxs-lookup"><span data-stu-id="56acb-104">Azure Blob storage is a service that stores unstructured data in the cloud as objects/blobs.</span></span> <span data-ttu-id="56acb-105">Magazyn obiektów blob można przechowywać dowolnego typu dane tekstowe lub binarne, takie jak dokument, plik multimedialny lub Instalator aplikacji.</span><span class="sxs-lookup"><span data-stu-id="56acb-105">Blob storage can store any type of text or binary data, such as a document, media file, or application installer.</span></span> <span data-ttu-id="56acb-106">Magazyn obiektów blob jest również określany jako magazyn obiektów.</span><span class="sxs-lookup"><span data-stu-id="56acb-106">Blob storage is also referred to as object storage.</span></span>

<span data-ttu-id="56acb-107">W tym artykule przedstawiono sposób wykonywania typowych zadań przy użyciu usługi Blob storage.</span><span class="sxs-lookup"><span data-stu-id="56acb-107">This article shows you how to perform common tasks using Blob storage.</span></span> <span data-ttu-id="56acb-108">Przykłady są zapisywane z użyciem F # za pomocą biblioteki klienta usługi Azure Storage dla platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="56acb-108">The samples are written using F# using the Azure Storage Client Library for .NET.</span></span> <span data-ttu-id="56acb-109">Zadania objęte obejmują jak przekazywanie, listy, pobieranie i usuwanie obiektów blob.</span><span class="sxs-lookup"><span data-stu-id="56acb-109">The tasks covered include how to upload, list, download, and delete blobs.</span></span>

<span data-ttu-id="56acb-110">Aby uzyskać omówienie pojęć dotyczących magazynu obiektów blob, zobacz [przewodnik platformy .NET dla usługi blob storage](/azure/storage/storage-dotnet-how-to-use-blobs).</span><span class="sxs-lookup"><span data-stu-id="56acb-110">For a conceptual overview of blob storage, see [the .NET guide for blob storage](/azure/storage/storage-dotnet-how-to-use-blobs).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="56acb-111">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="56acb-111">Prerequisites</span></span>

<span data-ttu-id="56acb-112">Aby użyć tego przewodnika, należy najpierw [Tworzenie konta usługi Azure storage](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="56acb-112">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span> <span data-ttu-id="56acb-113">Musisz mieć również klucz dostępu do magazynu dla tego konta.</span><span class="sxs-lookup"><span data-stu-id="56acb-113">You also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="56acb-114">Utwórz skrypt F # i Rozpocznij języka F # Interactive</span><span class="sxs-lookup"><span data-stu-id="56acb-114">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="56acb-115">Przykłady w tym artykule może służyć w aplikacji F # lub skryptu F #.</span><span class="sxs-lookup"><span data-stu-id="56acb-115">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="56acb-116">Aby utworzyć skrypt F #, Utwórz plik o `.fsx` rozszerzenia, na przykład `blobs.fsx`, w środowisku projektowym F #.</span><span class="sxs-lookup"><span data-stu-id="56acb-116">To create an F# script, create a file with the `.fsx` extension, for example `blobs.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="56acb-117">Następnie użyj [Menedżera pakietów](package-management.md) takich jak [Paket](https://fsprojects.github.io/Paket/) lub [NuGet](https://www.nuget.org/) zainstalował `WindowsAzure.Storage` i `Microsoft.WindowsAzure.ConfigurationManager` pakietów i odwołań `WindowsAzure.Storage.dll` i `Microsoft.WindowsAzure.Configuration.dll` przy użyciu skryptu `#r` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="56acb-117">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` and `Microsoft.WindowsAzure.ConfigurationManager` packages and reference `WindowsAzure.Storage.dll` and `Microsoft.WindowsAzure.Configuration.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="56acb-118">Dodawanie deklaracji przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="56acb-118">Add namespace declarations</span></span>

<span data-ttu-id="56acb-119">Dodaj następujący kod `open` instrukcji na górze `blobs.fsx` pliku:</span><span class="sxs-lookup"><span data-stu-id="56acb-119">Add the following `open` statements to the top of the `blobs.fsx` file:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="56acb-120">Pobieranie parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="56acb-120">Get your connection string</span></span>

<span data-ttu-id="56acb-121">Parametry połączenia usługi Azure Storage są potrzebne w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="56acb-121">You need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="56acb-122">Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz [skonfigurować parametry połączenia magazynu](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="56acb-122">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="56acb-123">Samouczek wprowadź parametry połączenia w skrypcie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="56acb-123">For the tutorial, you enter your connection string in your script, like this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

<span data-ttu-id="56acb-124">Jest to jednak **niezalecane** rzeczywiste projektów.</span><span class="sxs-lookup"><span data-stu-id="56acb-124">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="56acb-125">Klucz konta magazynu jest podobny do hasła głównego konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="56acb-125">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="56acb-126">Zawsze starannie Chroń klucz konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="56acb-126">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="56acb-127">Należy unikać, ich dystrybucję w innym użytkownikom, kodować je lub zapisanie go w pliku tekstowego, który jest dostępny dla innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="56acb-127">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="56acb-128">Można ponownie wygenerować klucz za pośrednictwem witryny Azure Portal, jeśli uważasz, że mogą zostać przejęte.</span><span class="sxs-lookup"><span data-stu-id="56acb-128">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="56acb-129">Rzeczywiste aplikacje najlepiej przechowywać parametry połączenia magazynu jest w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="56acb-129">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="56acb-130">Aby pobrać parametry połączenia z pliku konfiguracji, można to zrobić:</span><span class="sxs-lookup"><span data-stu-id="56acb-130">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

<span data-ttu-id="56acb-131">Użycie programu Azure Configuration Manager jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="56acb-131">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="56acb-132">Można również użyć interfejsu API, takich jak .NET Framework `ConfigurationManager` typu.</span><span class="sxs-lookup"><span data-stu-id="56acb-132">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="56acb-133">Przeanalizować parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="56acb-133">Parse the connection string</span></span>

<span data-ttu-id="56acb-134">Aby przeanalizować parametrów połączenia, należy użyć:</span><span class="sxs-lookup"><span data-stu-id="56acb-134">To parse the connection string, use:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

<span data-ttu-id="56acb-135">Spowoduje to zwrócenie `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="56acb-135">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-some-local-dummy-data"></a><span data-ttu-id="56acb-136">Tworzenie lokalnej fikcyjnego danych</span><span class="sxs-lookup"><span data-stu-id="56acb-136">Create some local dummy data</span></span>

<span data-ttu-id="56acb-137">Przed rozpoczęciem należy utworzyć pewnych fikcyjnego danych lokalnych w katalogu naszego skryptu.</span><span class="sxs-lookup"><span data-stu-id="56acb-137">Before you begin, create some dummy local data in the directory of our script.</span></span> <span data-ttu-id="56acb-138">Później możesz przekazać te dane.</span><span class="sxs-lookup"><span data-stu-id="56acb-138">Later you upload this data.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a><span data-ttu-id="56acb-139">Tworzenie klienta usługi obiektów Blob</span><span class="sxs-lookup"><span data-stu-id="56acb-139">Create the Blob service client</span></span>

<span data-ttu-id="56acb-140">`CloudBlobClient` Typu umożliwia pobieranie kontenerów i obiektów blob przechowywanych w magazynie obiektów Blob.</span><span class="sxs-lookup"><span data-stu-id="56acb-140">The `CloudBlobClient` type enables you to retrieve containers and blobs stored in Blob storage.</span></span> <span data-ttu-id="56acb-141">Oto jeden ze sposobów tworzenia klienta usługi:</span><span class="sxs-lookup"><span data-stu-id="56acb-141">Here's one way to create the service client:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

<span data-ttu-id="56acb-142">Teraz możesz przystąpić do pisania kodu, który odczytuje i zapisuje dane do magazynu obiektów Blob.</span><span class="sxs-lookup"><span data-stu-id="56acb-142">Now you are ready to write code that reads data from and writes data to Blob storage.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="56acb-143">Tworzenie kontenera</span><span class="sxs-lookup"><span data-stu-id="56acb-143">Create a container</span></span>

<span data-ttu-id="56acb-144">Ten przykład pokazuje, jak utworzyć kontener, jeśli jeszcze nie istnieje:</span><span class="sxs-lookup"><span data-stu-id="56acb-144">This example shows how to create a container if it does not already exist:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

<span data-ttu-id="56acb-145">Domyślnie nowy kontener jest prywatny, co oznacza, że musisz podać klucz dostępu do magazynu, aby pobierać obiekty BLOB z tego kontenera.</span><span class="sxs-lookup"><span data-stu-id="56acb-145">By default, the new container is private, meaning that you must specify your storage access key to download blobs from this container.</span></span> <span data-ttu-id="56acb-146">Jeśli chcesz udostępnić pliki znajdujące się w kontenerze wszystkim użytkownikom, można ustawić kontener jako publiczny, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="56acb-146">If you want to make the files within the container available to everyone, you can set the container to be public using the following code:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

<span data-ttu-id="56acb-147">Wszyscy użytkownicy Internetu mogą wyświetlać obiekty BLOB w kontenerze publicznym, ale użytkownik może je modyfikować lub usuwać tylko wtedy, gdy masz klucz dostępu do odpowiedniego konta lub sygnatury dostępu współdzielonego.</span><span class="sxs-lookup"><span data-stu-id="56acb-147">Anyone on the Internet can see blobs in a public container, but you can modify or delete them only if you have the appropriate account access key or a shared access signature.</span></span>

## <a name="upload-a-blob-into-a-container"></a><span data-ttu-id="56acb-148">Przekazywanie obiektu blob w kontenerze</span><span class="sxs-lookup"><span data-stu-id="56acb-148">Upload a blob into a container</span></span>

<span data-ttu-id="56acb-149">Usługa Azure Blob Storage obsługuje blokowe i stronicowe obiekty BLOB.</span><span class="sxs-lookup"><span data-stu-id="56acb-149">Azure Blob Storage supports block blobs and page blobs.</span></span> <span data-ttu-id="56acb-150">W większości przypadków blokowych obiektów blob to zalecany typ do użycia.</span><span class="sxs-lookup"><span data-stu-id="56acb-150">In most cases, a block blob is the recommended type to use.</span></span>

<span data-ttu-id="56acb-151">Aby przekazać plik do blokowego obiektu blob, Pobierz odwołanie do kontenera, a następnie użyj, aby uzyskać odwołanie do obiektu blob bloku.</span><span class="sxs-lookup"><span data-stu-id="56acb-151">To upload a file to a block blob, get a container reference and use it to get a block blob reference.</span></span> <span data-ttu-id="56acb-152">Po uzyskaniu odwołania do obiektu blob możesz przekazać dowolny strumień danych do niego, wywołując `UploadFromFile` metody.</span><span class="sxs-lookup"><span data-stu-id="56acb-152">Once you have a blob reference, you can upload any stream of data to it by calling the `UploadFromFile` method.</span></span> <span data-ttu-id="56acb-153">Ta operacja tworzy obiekt blob, jeśli nie została wcześniej istnieje, lub go zastąpić, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="56acb-153">This operation creates the blob if it didn't previously exist, or overwrite it if it does exist.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a><span data-ttu-id="56acb-154">Wyświetlanie listy obiektów blob w kontenerze</span><span class="sxs-lookup"><span data-stu-id="56acb-154">List the blobs in a container</span></span>

<span data-ttu-id="56acb-155">Aby wyświetlić listę obiektów blob w kontenerze, należy najpierw pobrać odwołanie do kontenera.</span><span class="sxs-lookup"><span data-stu-id="56acb-155">To list the blobs in a container, first get a container reference.</span></span> <span data-ttu-id="56acb-156">Następnie można użyć kontenera `ListBlobs` metodę, aby pobrać obiekty BLOB i/lub zawarte w nim katalogi.</span><span class="sxs-lookup"><span data-stu-id="56acb-156">You can then use the container's `ListBlobs` method to retrieve the blobs and/or directories within it.</span></span> <span data-ttu-id="56acb-157">Aby uzyskać dostęp z bogatego zestawu właściwości i metod zwróconego do `IListBlobItem`, należy rzutować go na `CloudBlockBlob`, `CloudPageBlob`, lub `CloudBlobDirectory` obiektu.</span><span class="sxs-lookup"><span data-stu-id="56acb-157">To access the rich set of properties and methods for a returned `IListBlobItem`, you must cast it to a `CloudBlockBlob`, `CloudPageBlob`, or `CloudBlobDirectory` object.</span></span> <span data-ttu-id="56acb-158">Jeśli typ jest nieznany, umożliwia sprawdzanie typu określić, do którego obiektu rzutować.</span><span class="sxs-lookup"><span data-stu-id="56acb-158">If the type is unknown, you can use a type check to determine which to cast it to.</span></span> <span data-ttu-id="56acb-159">Poniższy kod przedstawia sposób pobierania i zwracania identyfikatora URI poszczególnych elementów w `mydata` kontenera:</span><span class="sxs-lookup"><span data-stu-id="56acb-159">The following code demonstrates how to retrieve and output the URI of each item in the `mydata` container:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

<span data-ttu-id="56acb-160">Można również nazwy obiektów blob, zawierające informacje o ścieżce w nazwach.</span><span class="sxs-lookup"><span data-stu-id="56acb-160">You can also name blobs with path information in their names.</span></span> <span data-ttu-id="56acb-161">Spowoduje to utworzenie wirtualnej struktury katalogów, którą można organizować i przechodzić przez, tak jak w przypadku tradycyjnego systemu plików.</span><span class="sxs-lookup"><span data-stu-id="56acb-161">This creates a virtual directory structure that you can organize and traverse as you would a traditional file system.</span></span> <span data-ttu-id="56acb-162">Należy pamiętać, że struktura katalogów jest wyłącznie wirtualna — jedyne zasoby dostępne w usłudze Blob storage to kontenery i obiekty BLOB.</span><span class="sxs-lookup"><span data-stu-id="56acb-162">Note that the directory structure is virtual only - the only resources available in Blob storage are containers and blobs.</span></span> <span data-ttu-id="56acb-163">Jednak biblioteka klienta magazynu zapewnia `CloudBlobDirectory` obiekt, aby odwoływać się do katalogu wirtualnego i uprościć proces Praca z obiektami blob zorganizowanymi w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="56acb-163">However, the storage client library offers a `CloudBlobDirectory` object to refer to a virtual directory and simplify the process of working with blobs that are organized in this way.</span></span>

<span data-ttu-id="56acb-164">Na przykład rozważmy następujący zestaw blokowych obiektów blob w kontenerze o nazwie `photos`:</span><span class="sxs-lookup"><span data-stu-id="56acb-164">For example, consider the following set of block blobs in a container named `photos`:</span></span>

<span data-ttu-id="56acb-165">*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015/architecture/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg*
*2016/architecture/description.txt*
*2016/photo7.jpg*</span><span class="sxs-lookup"><span data-stu-id="56acb-165">*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015/architecture/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg*
*2016/architecture/description.txt*
*2016/photo7.jpg*</span></span>

<span data-ttu-id="56acb-166">Gdy wywołujesz `ListBlobs` na kontenerze (jak w powyższym przykładzie) zwrócenie listy hierarchicznej.</span><span class="sxs-lookup"><span data-stu-id="56acb-166">When you call `ListBlobs` on a container (as in the above sample), a hierarchical listing is returned.</span></span> <span data-ttu-id="56acb-167">Jeśli zawiera jednocześnie `CloudBlobDirectory` i `CloudBlockBlob` obiektów reprezentujących katalogi i obiekty BLOB w kontenerze, odpowiednio, a następnie wynikowe dane wyjściowe wyglądają podobnie do poniższego:</span><span class="sxs-lookup"><span data-stu-id="56acb-167">If it contains both `CloudBlobDirectory` and `CloudBlockBlob` objects, representing the directories and blobs in the container, respectively, then the resulting output looks similar to this:</span></span>

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

<span data-ttu-id="56acb-168">Opcjonalnie możesz ustawić `UseFlatBlobListing` parametru `ListBlobs` metody `true`.</span><span class="sxs-lookup"><span data-stu-id="56acb-168">Optionally, you can set the `UseFlatBlobListing` parameter of the `ListBlobs` method to `true`.</span></span> <span data-ttu-id="56acb-169">W takim przypadku każdy obiekt blob w kontenerze jest zwracana jako `CloudBlockBlob` obiektu.</span><span class="sxs-lookup"><span data-stu-id="56acb-169">In this case, every blob in the container is returned as a `CloudBlockBlob` object.</span></span> <span data-ttu-id="56acb-170">Wywołanie `ListBlobs` do zwrócenia listy niezhierarchizowanej wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="56acb-170">The call to `ListBlobs` to return a flat listing looks like this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

<span data-ttu-id="56acb-171">w zależności od bieżącej zawartości kontenera wyniki wyglądają następująco:</span><span class="sxs-lookup"><span data-stu-id="56acb-171">and, depending on the current contents of your container, the results look like this:</span></span>

```console
Block blob of length 4: https://<accountname>.blob.core.windows.net/photos/2015/architecture/description.txt
Block blob of length 314618: https://<accountname>.blob.core.windows.net/photos/2015/architecture/photo3.jpg
Block blob of length 522713: https://<accountname>.blob.core.windows.net/photos/2015/architecture/photo4.jpg
Block blob of length 4: https://<accountname>.blob.core.windows.net/photos/2016/architecture/description.txt
Block blob of length 419048: https://<accountname>.blob.core.windows.net/photos/2016/architecture/photo5.jpg
Block blob of length 506388: https://<accountname>.blob.core.windows.net/photos/2016/architecture/photo6.jpg
Block blob of length 399751: https://<accountname>.blob.core.windows.net/photos/2016/photo7.jpg
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

## <a name="download-blobs"></a><span data-ttu-id="56acb-172">Pobieranie obiektów blob</span><span class="sxs-lookup"><span data-stu-id="56acb-172">Download blobs</span></span>

<span data-ttu-id="56acb-173">Aby pobrać obiekty BLOB, należy najpierw pobrać odwołanie do obiektu blob, a następnie wywołać `DownloadToStream` metody.</span><span class="sxs-lookup"><span data-stu-id="56acb-173">To download blobs, first retrieve a blob reference and then call the `DownloadToStream` method.</span></span> <span data-ttu-id="56acb-174">W poniższym przykładzie użyto `DownloadToStream` metodę, aby przesłać zawartość obiektu blob do obiektu strumienia, który można następnie zachować w pliku lokalnym.</span><span class="sxs-lookup"><span data-stu-id="56acb-174">The following example uses the `DownloadToStream` method to transfer the blob contents to a stream object that you can then persist to a local file.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

<span data-ttu-id="56acb-175">Można również użyć `DownloadToStream` metody do pobierania zawartości obiektu blob jako ciąg tekstowy.</span><span class="sxs-lookup"><span data-stu-id="56acb-175">You can also use the `DownloadToStream` method to download the contents of a blob as a text string.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a><span data-ttu-id="56acb-176">Usuwanie obiektów blob</span><span class="sxs-lookup"><span data-stu-id="56acb-176">Delete blobs</span></span>

<span data-ttu-id="56acb-177">Aby usunąć obiekt blob, najpierw pobrać odwołanie do obiektu blob, a następnie wywołać `Delete` metody na nim.</span><span class="sxs-lookup"><span data-stu-id="56acb-177">To delete a blob, first get a blob reference and then call the `Delete` method on it.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a><span data-ttu-id="56acb-178">Wyświetlanie listy obiektów blob na stronach, asynchronicznie</span><span class="sxs-lookup"><span data-stu-id="56acb-178">List blobs in pages asynchronously</span></span>

<span data-ttu-id="56acb-179">Jeśli chcesz wyświetlić dużą liczbę obiektów blob lub chcesz kontrolować liczbę wyników zwracanych przez jedną operację wyświetlania listy, możesz wyświetlić listę obiektów blob na stronach wyników.</span><span class="sxs-lookup"><span data-stu-id="56acb-179">If you are listing a large number of blobs, or you want to control the number of results you return in one listing operation, you can list blobs in pages of results.</span></span> <span data-ttu-id="56acb-180">Ten przykład przedstawia sposób zwracania wyników na stronach asynchronicznie, dzięki czemu wykonanie nie jest blokowane podczas oczekiwania na zwrócenie dużych zestawów wyników.</span><span class="sxs-lookup"><span data-stu-id="56acb-180">This example shows how to return results in pages asynchronously, so that execution is not blocked while waiting to return a large set of results.</span></span>

<span data-ttu-id="56acb-181">W tym przykładzie przedstawiono niezhierarchizowaną listę obiektów blob, ale można również wykonać listę hierarchiczną, ustawiając `useFlatBlobListing` parametru `ListBlobsSegmentedAsync` metody `false`.</span><span class="sxs-lookup"><span data-stu-id="56acb-181">This example shows a flat blob listing, but you can also perform a hierarchical listing, by setting the `useFlatBlobListing` parameter of the `ListBlobsSegmentedAsync` method to `false`.</span></span>

<span data-ttu-id="56acb-182">Przykładowa aplikacja definiuje metodę asynchroniczną, za pomocą `async` bloku.</span><span class="sxs-lookup"><span data-stu-id="56acb-182">The sample defines an asynchronous method, using an `async` block.</span></span> <span data-ttu-id="56acb-183">``let!`` — Słowo kluczowe wstrzymuje wykonywanie przykładowej metody do momentu ukończenia zadania wyświetlania listy.</span><span class="sxs-lookup"><span data-stu-id="56acb-183">The ``let!`` keyword suspends execution of the sample method until the listing task completes.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

<span data-ttu-id="56acb-184">Firma Microsoft może teraz używać tej procedury asynchroniczne w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="56acb-184">We can now use this asynchronous routine as follows.</span></span> <span data-ttu-id="56acb-185">Najpierw należy przekazać fikcyjne dane (przy użyciu lokalnego pliku utworzone wcześniej w tym samouczku).</span><span class="sxs-lookup"><span data-stu-id="56acb-185">First you upload some dummy data (using the local file created earlier in this tutorial).</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

<span data-ttu-id="56acb-186">Teraz wywoła procedurę.</span><span class="sxs-lookup"><span data-stu-id="56acb-186">Now, call the routine.</span></span> <span data-ttu-id="56acb-187">Możesz użyć `Async.RunSynchronously` do wymuszenia wykonanie operacji asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="56acb-187">You use `Async.RunSynchronously` to force the execution of the asynchronous operation.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a><span data-ttu-id="56acb-188">Zapisywanie do uzupełnialnego obiektu blob</span><span class="sxs-lookup"><span data-stu-id="56acb-188">Writing to an append blob</span></span>

<span data-ttu-id="56acb-189">Uzupełnialny obiekt blob jest zoptymalizowany pod kątem operacji dołączania, takich jak rejestrowanie.</span><span class="sxs-lookup"><span data-stu-id="56acb-189">An append blob is optimized for append operations, such as logging.</span></span> <span data-ttu-id="56acb-190">Podobnie jak blokowy obiekt blob uzupełnialny obiekt blob jest złożony z bloków, ale po dodaniu nowego bloku do uzupełnialnego obiektu blob jest zawsze dołączany na końcu obiektu blob.</span><span class="sxs-lookup"><span data-stu-id="56acb-190">Like a block blob, an append blob is comprised of blocks, but when you add a new block to an append blob, it is always appended to the end of the blob.</span></span> <span data-ttu-id="56acb-191">Nie można zaktualizować ani usunąć istniejącego bloku w uzupełnialnym obiekcie blob.</span><span class="sxs-lookup"><span data-stu-id="56acb-191">You cannot update or delete an existing block in an append blob.</span></span> <span data-ttu-id="56acb-192">Identyfikatory bloków w uzupełnialnym obiekcie blob nie są widoczne, ponieważ są one dla blokowych obiektów blob.</span><span class="sxs-lookup"><span data-stu-id="56acb-192">The block IDs for an append blob are not exposed as they are for a block blob.</span></span>

<span data-ttu-id="56acb-193">Każdy blok w uzupełnialnym obiekcie blob może być inny rozmiar, maksymalnie do 4 MB, a uzupełnialny obiekt blob może zawierać maksymalnie 50 000 bloków.</span><span class="sxs-lookup"><span data-stu-id="56acb-193">Each block in an append blob can be a different size, up to a maximum of 4 MB, and an append blob can include a maximum of 50,000 blocks.</span></span> <span data-ttu-id="56acb-194">Maksymalny rozmiar uzupełnialnego obiektu blob w związku z tym jest nieco przekraczać 195 GB (4 MB X 50 000 bloków).</span><span class="sxs-lookup"><span data-stu-id="56acb-194">The maximum size of an append blob is therefore slightly more than 195 GB (4 MB X 50,000 blocks).</span></span>

<span data-ttu-id="56acb-195">Poniższy przykład tworzy nowy uzupełnialny obiekt blob i dołącza dane, symulując prostą operację rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="56acb-195">The following example creates a new append blob and appends some data to it, simulating a simple logging operation.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

<span data-ttu-id="56acb-196">Zobacz [omówienie blokowych obiektów blob, stronicowe obiekty BLOB i Uzupełnialnych obiektów blob](https://msdn.microsoft.com/library/azure/ee691964.aspx) Aby uzyskać więcej informacji na temat różnic między trzy typy obiektów blob.</span><span class="sxs-lookup"><span data-stu-id="56acb-196">See [Understanding Block Blobs, Page Blobs, and Append Blobs](https://msdn.microsoft.com/library/azure/ee691964.aspx) for more information about the differences between the three types of blobs.</span></span>

## <a name="concurrent-access"></a><span data-ttu-id="56acb-197">Równoczesny dostęp</span><span class="sxs-lookup"><span data-stu-id="56acb-197">Concurrent access</span></span>

<span data-ttu-id="56acb-198">Aby zapewnić obsługę równoczesny dostęp do obiektu blob z wielu klientów lub wielu wystąpień procesu, można użyć **elementów etag** lub **dzierżawy**.</span><span class="sxs-lookup"><span data-stu-id="56acb-198">To support concurrent access to a blob from multiple clients or multiple process instances, you can use **ETags** or **leases**.</span></span>

* <span data-ttu-id="56acb-199">**Element etag** — zapewnia sposób, aby wykryć, że obiekt blob lub kontenera została zmodyfikowana przez inny proces</span><span class="sxs-lookup"><span data-stu-id="56acb-199">**Etag** - provides a way to detect that the blob or container has been modified by another process</span></span>

* <span data-ttu-id="56acb-200">**Dzierżawy** — zapewnia sposób uzyskania wyłącznego, odnawialnych, zapisu i usuwania dostępu do obiektu blob przez pewien czas</span><span class="sxs-lookup"><span data-stu-id="56acb-200">**Lease** - provides a way to obtain exclusive, renewable, write or delete access to a blob for a period of time</span></span>

<span data-ttu-id="56acb-201">Aby uzyskać więcej informacji, zobacz [Zarządzanie współbieżnością w Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span><span class="sxs-lookup"><span data-stu-id="56acb-201">For more information, see [Managing Concurrency in Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span></span>

## <a name="naming-containers"></a><span data-ttu-id="56acb-202">Nazewnictwa kontenerów</span><span class="sxs-lookup"><span data-stu-id="56acb-202">Naming containers</span></span>

<span data-ttu-id="56acb-203">Każdy obiekt blob w usłudze Azure storage musi znajdować się w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="56acb-203">Every blob in Azure storage must reside in a container.</span></span> <span data-ttu-id="56acb-204">Kontener jest częścią nazwy obiektu blob.</span><span class="sxs-lookup"><span data-stu-id="56acb-204">The container forms part of the blob name.</span></span> <span data-ttu-id="56acb-205">Na przykład `mydata` to nazwa kontenera w tych przykładowych identyfikatorami URI obiektów blob:</span><span class="sxs-lookup"><span data-stu-id="56acb-205">For example, `mydata` is the name of the container in these sample blob URIs:</span></span>

    https://storagesample.blob.core.windows.net/mydata/blob1.txt
    https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

<span data-ttu-id="56acb-206">Nazwa kontenera musi być prawidłową nazwą DNS zgodną z następującymi zasadami nazewnictwa:</span><span class="sxs-lookup"><span data-stu-id="56acb-206">A container name must be a valid DNS name, conforming to the following naming rules:</span></span>

1. <span data-ttu-id="56acb-207">Nazwa kontenera musi zaczynać się literą lub cyfrą i może zawierać tylko litery, cyfry i znak kreski (-).</span><span class="sxs-lookup"><span data-stu-id="56acb-207">Container names must start with a letter or number, and can contain only letters, numbers, and the dash (-) character.</span></span>
1. <span data-ttu-id="56acb-208">Każdy znak kreski (-) musi być natychmiast poprzedzony i następuje litera lub cyfra; następujące po sobie kreski są niedozwolone w nazwach kontenerów.</span><span class="sxs-lookup"><span data-stu-id="56acb-208">Every dash (-) character must be immediately preceded and followed by a letter or number; consecutive dashes are not permitted in container names.</span></span>
1. <span data-ttu-id="56acb-209">Wszystkie litery w nazwie kontenera muszą być małe.</span><span class="sxs-lookup"><span data-stu-id="56acb-209">All letters in a container name must be lowercase.</span></span>
1. <span data-ttu-id="56acb-210">Nazwy kontenerów muszą być od 3 do 63 znaków.</span><span class="sxs-lookup"><span data-stu-id="56acb-210">Container names must be from 3 through 63 characters long.</span></span>

<span data-ttu-id="56acb-211">Należy pamiętać, że nazwa kontenera musi być zawsze małe litery.</span><span class="sxs-lookup"><span data-stu-id="56acb-211">Note that the name of a container must always be lowercase.</span></span> <span data-ttu-id="56acb-212">Jeśli zawierają wielkie litery w nazwie kontenera lub inny sposób naruszać zasady nazewnictwa dotyczące kontenerów zostaną, może wystąpić błąd 400 (nieprawidłowe żądanie).</span><span class="sxs-lookup"><span data-stu-id="56acb-212">If you include an upper-case letter in a container name, or otherwise violate the container naming rules, you may receive a 400 error (Bad Request).</span></span>

## <a name="managing-security-for-blobs"></a><span data-ttu-id="56acb-213">Zarządzanie zabezpieczeniami obiektów blob</span><span class="sxs-lookup"><span data-stu-id="56acb-213">Managing security for blobs</span></span>

<span data-ttu-id="56acb-214">Domyślnie usługi Azure Storage zapewnia bezpieczeństwo danych przez ograniczenie dostępu do właściciela konta, która jest w posiadaniu kluczy dostępu do konta.</span><span class="sxs-lookup"><span data-stu-id="56acb-214">By default, Azure Storage keeps your data secure by limiting access to the account owner, who is in possession of the account access keys.</span></span> <span data-ttu-id="56acb-215">Gdy zachodzi potrzeba udostępnienia danych obiektów blob na koncie magazynu, należy to zrobić bez uszczerbku dla bezpieczeństwa kluczy dostępu do Twojego konta.</span><span class="sxs-lookup"><span data-stu-id="56acb-215">When you need to share blob data in your storage account, it is important to do so without compromising the security of your account access keys.</span></span> <span data-ttu-id="56acb-216">Dodatkowo można zaszyfrować dane obiektu blob, aby zapewnić bezpieczeństwo podczas przesyłania przez sieć oraz w usłudze Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="56acb-216">Additionally, you can encrypt blob data to ensure that it is secure going over the wire and in Azure Storage.</span></span>

### <a name="controlling-access-to-blob-data"></a><span data-ttu-id="56acb-217">Kontrolowanie dostępu do danych obiektów blob</span><span class="sxs-lookup"><span data-stu-id="56acb-217">Controlling access to blob data</span></span>

<span data-ttu-id="56acb-218">Domyślnie dane obiektów blob na koncie magazynu jest dostępny tylko dla właściciela konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="56acb-218">By default, the blob data in your storage account is accessible only to storage account owner.</span></span> <span data-ttu-id="56acb-219">Uwierzytelnianie żądań dotyczących magazynu obiektów Blob wymaga klucza dostępu do konta, domyślnie.</span><span class="sxs-lookup"><span data-stu-id="56acb-219">Authenticating requests against Blob storage requires the account access key by default.</span></span> <span data-ttu-id="56acb-220">Można jednak udostępnić określone dane obiektów blob innym użytkownikom.</span><span class="sxs-lookup"><span data-stu-id="56acb-220">However, you might want to make certain blob data available to other users.</span></span>

<span data-ttu-id="56acb-221">Aby uzyskać szczegółowe informacje na temat kontrolowania dostępu do magazynu obiektów blob, zobacz [.NET — przewodnik dla sekcji magazyn obiektów blob na kontroli dostępu na](/azure/storage/storage-dotnet-how-to-use-blobs#controlling-access-to-blob-data).</span><span class="sxs-lookup"><span data-stu-id="56acb-221">For details on how to control access to blob storage, see [the .NET guide for blob storage section on access control](/azure/storage/storage-dotnet-how-to-use-blobs#controlling-access-to-blob-data).</span></span>


### <a name="encrypting-blob-data"></a><span data-ttu-id="56acb-222">Szyfrowanie danych obiektów blob</span><span class="sxs-lookup"><span data-stu-id="56acb-222">Encrypting blob data</span></span>

<span data-ttu-id="56acb-223">Usługa Azure Storage obsługuje szyfrowanie danych obiektów blob, zarówno na kliencie, jak i na serwerze.</span><span class="sxs-lookup"><span data-stu-id="56acb-223">Azure Storage supports encrypting blob data both at the client and on the server.</span></span>

<span data-ttu-id="56acb-224">Aby uzyskać więcej informacji na temat szyfrowania danych obiektów blob, zobacz [.NET — przewodnik dla sekcji magazyn obiektów blob na szyfrowaniu](/azure/storage/storage-dotnet-how-to-use-blobs#encrypting-blob-data).</span><span class="sxs-lookup"><span data-stu-id="56acb-224">For details on encrypting blob data, see [the .NET guide for blob storage section on encryption](/azure/storage/storage-dotnet-how-to-use-blobs#encrypting-blob-data).</span></span>

## <a name="next-steps"></a><span data-ttu-id="56acb-225">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="56acb-225">Next steps</span></span>

<span data-ttu-id="56acb-226">Teraz, kiedy znasz już podstawy usługi Blob storage, skorzystaj z poniższych linków, aby dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="56acb-226">Now that you've learned the basics of Blob storage, follow these links to learn more.</span></span>

### <a name="tools"></a><span data-ttu-id="56acb-227">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="56acb-227">Tools</span></span>
- <span data-ttu-id="56acb-228">[F # AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/) F # dostawcy typu, który może służyć do zapoznaj się z zasobami obiektów Blob, tabel i kolejek usługi Azure Storage i z łatwością zastosować operacji CRUD na nich.</span><span class="sxs-lookup"><span data-stu-id="56acb-228">[F# AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/) An F# Type Provider which can be used to explore Blob, Table and Queue Azure Storage assets and easily apply CRUD operations on them.</span></span>
- <span data-ttu-id="56acb-229">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage) F # interfejsu API przy użyciu usługi Microsoft Azure Table Storage</span><span class="sxs-lookup"><span data-stu-id="56acb-229">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage) An F# API for using Microsoft Azure Table Storage service</span></span>
- <span data-ttu-id="56acb-230">[Microsoft Azure Storage Explorer Poglądową](/azure/vs-azure-tools-storage-manage-with-storage-explorer) jest bezpłatną, autonomiczną aplikacją oferowaną przez firmę Microsoft, która umożliwia wizualną pracę z danymi usługi Azure Storage w Windows, OS X i Linux.</span><span class="sxs-lookup"><span data-stu-id="56acb-230">[Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer) is a free, standalone app from Microsoft that enables you to work visually with Azure Storage data on Windows, OS X, and Linux.</span></span>

### <a name="blob-storage-reference"></a><span data-ttu-id="56acb-231">Odwołanie do obiektu blob magazynu</span><span class="sxs-lookup"><span data-stu-id="56acb-231">Blob storage reference</span></span>

- [<span data-ttu-id="56acb-232">Interfejsy API usługi Azure Storage dla platformy .NET</span><span class="sxs-lookup"><span data-stu-id="56acb-232">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="56acb-233">Dokumentacja interfejsu API REST usługi Azure Storage</span><span class="sxs-lookup"><span data-stu-id="56acb-233">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)

### <a name="related-guides"></a><span data-ttu-id="56acb-234">Powiązane przewodniki</span><span class="sxs-lookup"><span data-stu-id="56acb-234">Related guides</span></span>

- [<span data-ttu-id="56acb-235">Wprowadzenie do usługi Azure Blob Storage w języku C#</span><span class="sxs-lookup"><span data-stu-id="56acb-235">Getting Started with Azure Blob Storage in C#</span></span>](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/)
- [<span data-ttu-id="56acb-236">Transferowanie danych za pomocą narzędzia wiersza polecenia AzCopy w Windows</span><span class="sxs-lookup"><span data-stu-id="56acb-236">Transfer data with the AzCopy command-line utility on Windows</span></span>](/azure/storage/common/storage-use-azcopy)
- [<span data-ttu-id="56acb-237">Transferowanie danych za pomocą narzędzia wiersza polecenia AzCopy w systemie Linux</span><span class="sxs-lookup"><span data-stu-id="56acb-237">Transfer data with the AzCopy command-line utility on Linux</span></span>](/azure/storage/common/storage-use-azcopy-linux)
- [<span data-ttu-id="56acb-238">Konfigurowanie parametrów połączenia usługi Azure Storage</span><span class="sxs-lookup"><span data-stu-id="56acb-238">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="56acb-239">Blog zespołu usługi Azure Storage</span><span class="sxs-lookup"><span data-stu-id="56acb-239">Azure Storage Team Blog</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/)
