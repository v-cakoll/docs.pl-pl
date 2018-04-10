---
title: 'Rozpoczynanie pracy z magazynem obiektów Blob platformy Azure przy użyciu języka F #'
description: Przechowuj dane niestrukturalne w chmurze za pomocą magazynu obiektów Blob platformy Azure.
keywords: visual f#, f#, functional programming, .NET, .NET Core, Azure
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c5b74a4f-dcd1-4849-930c-904b6c8a04e1
ms.openlocfilehash: 14ccba36638c724536793a6a589cf1c0a6186eeb
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="get-started-with-azure-blob-storage-using-f"></a><span data-ttu-id="1d8ba-104">Rozpoczynanie pracy z magazynem obiektów Blob platformy Azure przy użyciu języka F #</span><span class="sxs-lookup"><span data-stu-id="1d8ba-104">Get started with Azure Blob storage using F#</span></span> #

<span data-ttu-id="1d8ba-105">Magazyn obiektów Blob Azure to usługa, która przechowywania danych niestrukturalnych w chmurze w postaci obiektów blob.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-105">Azure Blob storage is a service that stores unstructured data in the cloud as objects/blobs.</span></span> <span data-ttu-id="1d8ba-106">Magazyn obiektów blob umożliwia przechowywanie dowolnego typu tekstu lub danych binarnych, takich jak dokument, plik multimedialny lub Instalator aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-106">Blob storage can store any type of text or binary data, such as a document, media file, or application installer.</span></span> <span data-ttu-id="1d8ba-107">Magazyn obiektów blob jest również nazywany magazynem obiektów.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-107">Blob storage is also referred to as object storage.</span></span>

<span data-ttu-id="1d8ba-108">W tym artykule przedstawiono sposób wykonywania typowych zadań przy użyciu magazynu obiektów Blob.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-108">This article shows you how to perform common tasks using Blob storage.</span></span> <span data-ttu-id="1d8ba-109">Przykłady są napisane przy użyciu F # za pomocą biblioteki klienta magazynu Azure dla platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-109">The samples are written using F# using the Azure Storage Client Library for .NET.</span></span> <span data-ttu-id="1d8ba-110">Zadania, jest objęty obejmują jak przekazywanie, listy, pobieranie i usuwanie obiektów blob.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-110">The tasks covered include how to upload, list, download, and delete blobs.</span></span>

<span data-ttu-id="1d8ba-111">Omówienie koncepcji magazynu obiektów blob, zobacz [przewodnik .NET dla magazynu obiektów blob](/azure/storage/storage-dotnet-how-to-use-blobs).</span><span class="sxs-lookup"><span data-stu-id="1d8ba-111">For a conceptual overview of blob storage, see [the .NET guide for blob storage](/azure/storage/storage-dotnet-how-to-use-blobs).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1d8ba-112">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="1d8ba-112">Prerequisites</span></span>

<span data-ttu-id="1d8ba-113">Aby użyć tego przewodnika, należy najpierw [utworzyć konto magazynu Azure](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="1d8ba-113">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span> <span data-ttu-id="1d8ba-114">Należy również klucz dostępu do magazynu dla tego konta.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-114">You also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="1d8ba-115">Tworzenie skryptu języka F # i rozpocząć F # Interactive</span><span class="sxs-lookup"><span data-stu-id="1d8ba-115">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="1d8ba-116">Przykłady w tym artykule można używać w F # aplikacji lub skryptu języka F #.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-116">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="1d8ba-117">Aby utworzyć skrypt F #, Utwórz plik o `.fsx` rozszerzenie, na przykład `blobs.fsx`, w środowiska deweloperskiego F #.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-117">To create an F# script, create a file with the `.fsx` extension, for example `blobs.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="1d8ba-118">Następnie użyj [Menedżera pakietów](package-management.md) takich jak [Paket](https://fsprojects.github.io/Paket/) lub [NuGet](https://www.nuget.org/) do zainstalowania `WindowsAzure.Storage` i `Microsoft.WindowsAzure.ConfigurationManager` pakietów i odwołanie `WindowsAzure.Storage.dll` i `Microsoft.WindowsAzure.Configuration.dll` w za pomocą skryptu `#r` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-118">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` and `Microsoft.WindowsAzure.ConfigurationManager` packages and reference `WindowsAzure.Storage.dll` and `Microsoft.WindowsAzure.Configuration.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="1d8ba-119">Dodawanie deklaracji przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="1d8ba-119">Add namespace declarations</span></span>

<span data-ttu-id="1d8ba-120">Dodaj następujące `open` instrukcje na początku `blobs.fsx` pliku:</span><span class="sxs-lookup"><span data-stu-id="1d8ba-120">Add the following `open` statements to the top of the `blobs.fsx` file:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="1d8ba-121">Pobierz ciąg połączenia</span><span class="sxs-lookup"><span data-stu-id="1d8ba-121">Get your connection string</span></span>

<span data-ttu-id="1d8ba-122">Parametry połączenia magazynu Azure są wymagane dla tego samouczka.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-122">You need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="1d8ba-123">Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz [skonfigurować parametry połączenia magazynu](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="1d8ba-123">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="1d8ba-124">Samouczek możesz wprowadzić parametry połączenia za pomocą skryptu, jak to:</span><span class="sxs-lookup"><span data-stu-id="1d8ba-124">For the tutorial, you enter your connection string in your script, like this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

<span data-ttu-id="1d8ba-125">Jest to jednak **niezalecane** rzeczywiste projektów.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-125">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="1d8ba-126">Klucz konta magazynu jest podobny do hasła głównego konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-126">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="1d8ba-127">Zawsze starannie Chroń klucz konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-127">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="1d8ba-128">Unikaj udostępniaj go innym użytkownikom, kodować je lub zapisać go w pliku jako zwykły tekst, który jest dostępny do innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-128">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="1d8ba-129">Można ponownie wygenerować klucz przy użyciu portalu Azure, jeśli uważasz, że mogą zostać naruszone.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-129">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="1d8ba-130">Rzeczywiste aplikacje najlepiej przechowywać parametry połączenia magazynu jest w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-130">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="1d8ba-131">Aby pobrać parametry połączenia w pliku konfiguracji, można to zrobić:</span><span class="sxs-lookup"><span data-stu-id="1d8ba-131">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

<span data-ttu-id="1d8ba-132">Przy użyciu programu Azure Configuration Manager jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-132">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="1d8ba-133">Można również użyć interfejsu API, takich jak .NET Framework `ConfigurationManager` typu.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-133">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="1d8ba-134">Przeanalizować parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="1d8ba-134">Parse the connection string</span></span>

<span data-ttu-id="1d8ba-135">Aby przeanalizować parametrów połączenia, należy użyć:</span><span class="sxs-lookup"><span data-stu-id="1d8ba-135">To parse the connection string, use:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

<span data-ttu-id="1d8ba-136">To polecenie zwróci `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-136">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-some-local-dummy-data"></a><span data-ttu-id="1d8ba-137">Tworzenie niektórych fikcyjny dane lokalne</span><span class="sxs-lookup"><span data-stu-id="1d8ba-137">Create some local dummy data</span></span>

<span data-ttu-id="1d8ba-138">Przed rozpoczęciem należy utworzyć niektórych fikcyjny danych lokalnych w katalogu naszych skryptu.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-138">Before you begin, create some dummy local data in the directory of our script.</span></span> <span data-ttu-id="1d8ba-139">Później możesz przekazać dane.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-139">Later you upload this data.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a><span data-ttu-id="1d8ba-140">Tworzenie klienta usługi Blob</span><span class="sxs-lookup"><span data-stu-id="1d8ba-140">Create the Blob service client</span></span>

<span data-ttu-id="1d8ba-141">`CloudBlobClient` Typu umożliwia pobieranie kontenerów i obiektów blob przechowywanych w magazynie obiektów Blob.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-141">The `CloudBlobClient` type enables you to retrieve containers and blobs stored in Blob storage.</span></span> <span data-ttu-id="1d8ba-142">Oto jeden ze sposobów tworzenia klienta usługi:</span><span class="sxs-lookup"><span data-stu-id="1d8ba-142">Here's one way to create the service client:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

<span data-ttu-id="1d8ba-143">Teraz można przystąpić do pisania kodu, która odczytuje i zapisuje dane do magazynu obiektów Blob.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-143">Now you are ready to write code that reads data from and writes data to Blob storage.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="1d8ba-144">Tworzenie kontenera</span><span class="sxs-lookup"><span data-stu-id="1d8ba-144">Create a container</span></span>

<span data-ttu-id="1d8ba-145">W tym przykładzie pokazano, jak utworzyć kontener, jeśli jeszcze nie istnieje:</span><span class="sxs-lookup"><span data-stu-id="1d8ba-145">This example shows how to create a container if it does not already exist:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

<span data-ttu-id="1d8ba-146">Domyślnie nowy kontener jest prywatny, co oznacza, że należy określić klucz dostępu do magazynu, aby pobierać obiekty BLOB z tego kontenera.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-146">By default, the new container is private, meaning that you must specify your storage access key to download blobs from this container.</span></span> <span data-ttu-id="1d8ba-147">Jeśli chcesz udostępnić pliki w kontenerze wszystkim użytkownikom, możesz ustawić kontener jako publiczny przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="1d8ba-147">If you want to make the files within the container available to everyone, you can set the container to be public using the following code:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

<span data-ttu-id="1d8ba-148">Wszyscy użytkownicy Internetu mogą wyświetlać obiekty BLOB w kontenerze publicznym, ale można zmodyfikować lub usunąć je tylko wtedy, gdy klucz dostępu do odpowiedniego konta lub sygnatury dostępu współdzielonego.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-148">Anyone on the Internet can see blobs in a public container, but you can modify or delete them only if you have the appropriate account access key or a shared access signature.</span></span>

## <a name="upload-a-blob-into-a-container"></a><span data-ttu-id="1d8ba-149">Przekazywanie obiektu blob do kontenera</span><span class="sxs-lookup"><span data-stu-id="1d8ba-149">Upload a blob into a container</span></span>

<span data-ttu-id="1d8ba-150">Azure Blob Storage obsługuje blokowe i stronicowe obiekty BLOB.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-150">Azure Blob Storage supports block blobs and page blobs.</span></span> <span data-ttu-id="1d8ba-151">W większości przypadków blokowych obiektów blob jest zalecany typ do użycia.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-151">In most cases, a block blob is the recommended type to use.</span></span>

<span data-ttu-id="1d8ba-152">Aby przekazać plik do blokowego obiektu blob, Pobierz odwołanie do kontenera i użyj go, aby pobrać odwołanie do obiektu blob bloku.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-152">To upload a file to a block blob, get a container reference and use it to get a block blob reference.</span></span> <span data-ttu-id="1d8ba-153">Po utworzeniu odwołanie do obiektu blob, dowolny strumień danych można przekazać do niej przez wywołanie metody `UploadFromFile` metody.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-153">Once you have a blob reference, you can upload any stream of data to it by calling the `UploadFromFile` method.</span></span> <span data-ttu-id="1d8ba-154">Ta operacja tworzy obiektu blob, jeśli on nie istnieje, lub go zastąpić, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-154">This operation creates the blob if it didn't previously exist, or overwrite it if it does exist.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a><span data-ttu-id="1d8ba-155">Wyświetlanie obiektów blob w kontenerze</span><span class="sxs-lookup"><span data-stu-id="1d8ba-155">List the blobs in a container</span></span>

<span data-ttu-id="1d8ba-156">Aby wyświetlić listę obiektów blob w kontenerze, należy najpierw pobrać odwołanie do kontenera.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-156">To list the blobs in a container, first get a container reference.</span></span> <span data-ttu-id="1d8ba-157">Następnie można użyć kontenera `ListBlobs` metodę, aby pobrać obiekty BLOB i/lub zawarte w nim katalogi.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-157">You can then use the container's `ListBlobs` method to retrieve the blobs and/or directories within it.</span></span> <span data-ttu-id="1d8ba-158">Aby dostęp do bogatego zestawu właściwości i metod zwróconego `IListBlobItem`, należy rzutować go do `CloudBlockBlob`, `CloudPageBlob`, lub `CloudBlobDirectory` obiektu.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-158">To access the rich set of properties and methods for a returned `IListBlobItem`, you must cast it to a `CloudBlockBlob`, `CloudPageBlob`, or `CloudBlobDirectory` object.</span></span> <span data-ttu-id="1d8ba-159">Jeśli typ jest nieznany, umożliwia sprawdzanie typu określenie, które można rzutować na.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-159">If the type is unknown, you can use a type check to determine which to cast it to.</span></span> <span data-ttu-id="1d8ba-160">Poniższy kod przedstawia sposób pobierania i zwracania identyfikatora URI poszczególnych elementów w `mydata` kontenera:</span><span class="sxs-lookup"><span data-stu-id="1d8ba-160">The following code demonstrates how to retrieve and output the URI of each item in the `mydata` container:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

<span data-ttu-id="1d8ba-161">Można także obiekty BLOB nazwy zawierające informacje o ścieżce ich nazw.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-161">You can also name blobs with path information in their names.</span></span> <span data-ttu-id="1d8ba-162">Spowoduje to utworzenie wirtualnej struktury katalogów, które można organizować i przechodzić między nimi tak jak w przypadku tradycyjnego systemu plików.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-162">This creates a virtual directory structure that you can organize and traverse as you would a traditional file system.</span></span> <span data-ttu-id="1d8ba-163">Należy pamiętać, że struktura katalogów jest wyłącznie wirtualna — jedyne zasoby dostępne w magazynie obiektów Blob to kontenery i obiekty BLOB.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-163">Note that the directory structure is virtual only - the only resources available in Blob storage are containers and blobs.</span></span> <span data-ttu-id="1d8ba-164">Jednak biblioteka klienta magazynu zapewnia `CloudBlobDirectory` obiekt, aby odwoływać się do katalogu wirtualnego i uprościć proces Praca z obiektami blob zorganizowanymi w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-164">However, the storage client library offers a `CloudBlobDirectory` object to refer to a virtual directory and simplify the process of working with blobs that are organized in this way.</span></span>

<span data-ttu-id="1d8ba-165">Rozważmy na przykład następujący zestaw blokowych obiektów blob w kontenerze o nazwie `photos`:</span><span class="sxs-lookup"><span data-stu-id="1d8ba-165">For example, consider the following set of block blobs in a container named `photos`:</span></span>

<span data-ttu-id="1d8ba-166">*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015/architecture/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg*
*2016/architecture/description.txt*
*2016/photo7.jpg*</span><span class="sxs-lookup"><span data-stu-id="1d8ba-166">*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015/architecture/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg*
*2016/architecture/description.txt*
*2016/photo7.jpg*</span></span>

<span data-ttu-id="1d8ba-167">Podczas wywoływania `ListBlobs` kontenera (jak w powyższym przykładzie), zwrócenie listy hierarchicznej.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-167">When you call `ListBlobs` on a container (as in the above sample), a hierarchical listing is returned.</span></span> <span data-ttu-id="1d8ba-168">Jeśli oba zawiera `CloudBlobDirectory` i `CloudBlockBlob` obiektów reprezentujących katalogi i obiekty BLOB w kontenerze, odpowiednio, a następnie dane wyjściowe podobny do poniższego:</span><span class="sxs-lookup"><span data-stu-id="1d8ba-168">If it contains both `CloudBlobDirectory` and `CloudBlockBlob` objects, representing the directories and blobs in the container, respectively, then the resulting output looks similar to this:</span></span>

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

<span data-ttu-id="1d8ba-169">Opcjonalnie można ustawić `UseFlatBlobListing` parametr `ListBlobs` metodę `true`.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-169">Optionally, you can set the `UseFlatBlobListing` parameter of the `ListBlobs` method to `true`.</span></span> <span data-ttu-id="1d8ba-170">W takim przypadku każdy obiekt blob w kontenerze jest zwracana jako `CloudBlockBlob` obiektu.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-170">In this case, every blob in the container is returned as a `CloudBlockBlob` object.</span></span> <span data-ttu-id="1d8ba-171">Wywołanie `ListBlobs` do zwrócenia listy niezhierarchizowanej wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="1d8ba-171">The call to `ListBlobs` to return a flat listing looks like this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

<span data-ttu-id="1d8ba-172">i, w zależności od bieżącej zawartości z kontenera wyniki wyglądają następująco:</span><span class="sxs-lookup"><span data-stu-id="1d8ba-172">and, depending on the current contents of your container, the results look like this:</span></span>

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

## <a name="download-blobs"></a><span data-ttu-id="1d8ba-173">Pobieranie obiektów blob</span><span class="sxs-lookup"><span data-stu-id="1d8ba-173">Download blobs</span></span>

<span data-ttu-id="1d8ba-174">Aby pobrać obiekty BLOB, należy najpierw pobrać odwołanie do obiektu blob, a następnie wywołać `DownloadToStream` metody.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-174">To download blobs, first retrieve a blob reference and then call the `DownloadToStream` method.</span></span> <span data-ttu-id="1d8ba-175">W poniższym przykładzie użyto `DownloadToStream` metodę, aby przesłać zawartość obiektu blob do obiektu strumienia, który można następnie zachować do pliku lokalnego.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-175">The following example uses the `DownloadToStream` method to transfer the blob contents to a stream object that you can then persist to a local file.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

<span data-ttu-id="1d8ba-176">Można również użyć `DownloadToStream` metodę, aby pobrać zawartość obiektu blob jako ciąg tekstowy.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-176">You can also use the `DownloadToStream` method to download the contents of a blob as a text string.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a><span data-ttu-id="1d8ba-177">Usuwanie obiektów blob</span><span class="sxs-lookup"><span data-stu-id="1d8ba-177">Delete blobs</span></span>

<span data-ttu-id="1d8ba-178">Aby usunąć obiekt blob, najpierw pobrać odwołanie do obiektu blob, a następnie wywołać `Delete` dla niego metodę.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-178">To delete a blob, first get a blob reference and then call the `Delete` method on it.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a><span data-ttu-id="1d8ba-179">Asynchroniczne wyświetlanie obiektów blob na stronach</span><span class="sxs-lookup"><span data-stu-id="1d8ba-179">List blobs in pages asynchronously</span></span>

<span data-ttu-id="1d8ba-180">Jeśli chcesz wyświetlić dużą liczbę obiektów blob lub chcesz kontrolować liczbę wyników zwracanych przez jedną operację wyświetlania listy, można wyświetlić listę obiektów blob na stronach wyników.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-180">If you are listing a large number of blobs, or you want to control the number of results you return in one listing operation, you can list blobs in pages of results.</span></span> <span data-ttu-id="1d8ba-181">Ten przykład przedstawia sposób zwracania wyników na stronach asynchronicznie, dzięki czemu wykonanie nie jest blokowane podczas oczekiwania na zwrócenie dużych zestawów wyników.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-181">This example shows how to return results in pages asynchronously, so that execution is not blocked while waiting to return a large set of results.</span></span>

<span data-ttu-id="1d8ba-182">W tym przykładzie przedstawiono niezhierarchizowaną listę obiektów blob, ale można również wykonywać listę hierarchiczną, ustawiając `useFlatBlobListing` parametr `ListBlobsSegmentedAsync` metodę `false`.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-182">This example shows a flat blob listing, but you can also perform a hierarchical listing, by setting the `useFlatBlobListing` parameter of the `ListBlobsSegmentedAsync` method to `false`.</span></span>

<span data-ttu-id="1d8ba-183">Przykład definiuje metodę asynchroniczną, przy użyciu `async` bloku.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-183">The sample defines an asynchronous method, using an `async` block.</span></span> <span data-ttu-id="1d8ba-184">``let!`` — Słowo kluczowe wstrzymuje wykonywanie przykładowej metody do momentu ukończenia zadania wyświetlania listy.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-184">The ``let!`` keyword suspends execution of the sample method until the listing task completes.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

<span data-ttu-id="1d8ba-185">Firma Microsoft mogą teraz używać tej procedury asynchronicznych w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-185">We can now use this asynchronous routine as follows.</span></span> <span data-ttu-id="1d8ba-186">Najpierw należy przekazywania danych zastępczego (przy użyciu lokalnego pliku utworzona we wcześniejszej części tego samouczka).</span><span class="sxs-lookup"><span data-stu-id="1d8ba-186">First you upload some dummy data (using the local file created earlier in this tutorial).</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

<span data-ttu-id="1d8ba-187">Teraz wywoła procedurę.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-187">Now, call the routine.</span></span> <span data-ttu-id="1d8ba-188">Możesz użyć ``Async.RunSynchronously`` Aby wymusić wykonanie operacji asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-188">You use ``Async.RunSynchronously`` to force the execution of the asynchronous operation.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a><span data-ttu-id="1d8ba-189">Zapisywanie do uzupełnialnego obiektu blob</span><span class="sxs-lookup"><span data-stu-id="1d8ba-189">Writing to an append blob</span></span>

<span data-ttu-id="1d8ba-190">Uzupełnialny obiekt blob jest zoptymalizowana pod kątem operacji dołączania, takich jak rejestrowanie.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-190">An append blob is optimized for append operations, such as logging.</span></span> <span data-ttu-id="1d8ba-191">Podobnie jak blokowy obiekt blob uzupełnialny obiekt blob jest złożony z bloków, ale po dodaniu nowego bloku do uzupełnialnego obiektu blob jest zawsze dołączany na końcu obiektu blob.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-191">Like a block blob, an append blob is comprised of blocks, but when you add a new block to an append blob, it is always appended to the end of the blob.</span></span> <span data-ttu-id="1d8ba-192">Nie można zaktualizować lub usunąć istniejącego bloku w uzupełnialnym obiekcie blob.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-192">You cannot update or delete an existing block in an append blob.</span></span> <span data-ttu-id="1d8ba-193">Identyfikatory bloków w uzupełnialnym obiekcie blob nie są widoczne, jak w przypadku blokowego obiektu blob.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-193">The block IDs for an append blob are not exposed as they are for a block blob.</span></span>

<span data-ttu-id="1d8ba-194">Każdy blok w uzupełnialnym obiekcie blob może być inny rozmiar maksymalnie 4 MB, a uzupełnialny obiekt blob może zawierać maksymalnie 50 000 bloków.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-194">Each block in an append blob can be a different size, up to a maximum of 4 MB, and an append blob can include a maximum of 50,000 blocks.</span></span> <span data-ttu-id="1d8ba-195">Maksymalny rozmiar uzupełnialnego obiektu blob w związku z tym jest nieco przekraczać 195 GB (4 MB X 50 000 bloków).</span><span class="sxs-lookup"><span data-stu-id="1d8ba-195">The maximum size of an append blob is therefore slightly more than 195 GB (4 MB X 50,000 blocks).</span></span>

<span data-ttu-id="1d8ba-196">Poniższy przykład tworzy nowy uzupełnialny obiekt blob i dołącza niektóre dane, symulując prostą operację rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-196">The following example creates a new append blob and appends some data to it, simulating a simple logging operation.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

<span data-ttu-id="1d8ba-197">Zobacz [opis blokowe, stronicowe obiekty BLOB i Dołącz obiektów blob](https://msdn.microsoft.com/library/azure/ee691964.aspx) Aby uzyskać więcej informacji o różnicach między tymi trzema typami obiektów blob.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-197">See [Understanding Block Blobs, Page Blobs, and Append Blobs](https://msdn.microsoft.com/library/azure/ee691964.aspx) for more information about the differences between the three types of blobs.</span></span>

## <a name="concurrent-access"></a><span data-ttu-id="1d8ba-198">Współbieżny dostęp</span><span class="sxs-lookup"><span data-stu-id="1d8ba-198">Concurrent access</span></span>

<span data-ttu-id="1d8ba-199">Aby obsługiwać równoczesny dostęp do obiektu blob z wielu klientów lub wielu wystąpień procesu, można użyć **elementy etag** lub **dzierżawy**.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-199">To support concurrent access to a blob from multiple clients or multiple process instances, you can use **ETags** or **leases**.</span></span>

* <span data-ttu-id="1d8ba-200">**Element etag** — pozwala wykryć, że obiekt blob lub kontener został zmodyfikowany przez inny proces</span><span class="sxs-lookup"><span data-stu-id="1d8ba-200">**Etag** - provides a way to detect that the blob or container has been modified by another process</span></span>

* <span data-ttu-id="1d8ba-201">**Dzierżawy** — pozwala uzyskać wyłącznej, odnawialnymi, zapisu albo usuwania dostępu do obiektu blob w danym okresie czasu</span><span class="sxs-lookup"><span data-stu-id="1d8ba-201">**Lease** - provides a way to obtain exclusive, renewable, write or delete access to a blob for a period of time</span></span>

<span data-ttu-id="1d8ba-202">Aby uzyskać więcej informacji, zobacz [Zarządzanie współbieżność w magazynie platformy Microsoft Azure](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span><span class="sxs-lookup"><span data-stu-id="1d8ba-202">For more information, see [Managing Concurrency in Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span></span>

## <a name="naming-containers"></a><span data-ttu-id="1d8ba-203">Kontenery nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="1d8ba-203">Naming containers</span></span>

<span data-ttu-id="1d8ba-204">Każdy obiekt blob w magazynie Azure musi znajdować się w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-204">Every blob in Azure storage must reside in a container.</span></span> <span data-ttu-id="1d8ba-205">Kontener jest częścią nazwy obiektu blob.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-205">The container forms part of the blob name.</span></span> <span data-ttu-id="1d8ba-206">Na przykład `mydata` to nazwa kontenera w tych przykładowych identyfikatorach URI obiektów blob:</span><span class="sxs-lookup"><span data-stu-id="1d8ba-206">For example, `mydata` is the name of the container in these sample blob URIs:</span></span>

    https://storagesample.blob.core.windows.net/mydata/blob1.txt
    https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

<span data-ttu-id="1d8ba-207">Nazwa kontenera musi być prawidłową nazwą DNS zgodną z następującymi zasadami nazewnictwa:</span><span class="sxs-lookup"><span data-stu-id="1d8ba-207">A container name must be a valid DNS name, conforming to the following naming rules:</span></span>

1. <span data-ttu-id="1d8ba-208">Nazwy kontenerów muszą zaczynać się literą lub cyfrą i może zawierać tylko litery, cyfry i znak kreski (-).</span><span class="sxs-lookup"><span data-stu-id="1d8ba-208">Container names must start with a letter or number, and can contain only letters, numbers, and the dash (-) character.</span></span>
1. <span data-ttu-id="1d8ba-209">Każdy znak kreski (-) musi być od razu poprzedzone i następuje literą lub cyfrą; następujących po sobie kresek nie są dozwolone w nazwach kontenerów.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-209">Every dash (-) character must be immediately preceded and followed by a letter or number; consecutive dashes are not permitted in container names.</span></span>
1. <span data-ttu-id="1d8ba-210">Wszystkie litery w nazwie kontenera muszą być małymi literami.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-210">All letters in a container name must be lowercase.</span></span>
1. <span data-ttu-id="1d8ba-211">Nazwy kontenerów muszą mieć od 3 do 63 znaków.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-211">Container names must be from 3 through 63 characters long.</span></span>

<span data-ttu-id="1d8ba-212">Należy pamiętać, że nazwa kontenera musi być zawsze małe litery.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-212">Note that the name of a container must always be lowercase.</span></span> <span data-ttu-id="1d8ba-213">Jeśli zawierać wielką literę w nazwie kontenera lub reguły nazewnictwa dotyczące kontenerów zostaną naruszone w przeciwnym razie, może zostać wyświetlony błąd 400 (nieprawidłowe żądanie).</span><span class="sxs-lookup"><span data-stu-id="1d8ba-213">If you include an upper-case letter in a container name, or otherwise violate the container naming rules, you may receive a 400 error (Bad Request).</span></span>

## <a name="managing-security-for-blobs"></a><span data-ttu-id="1d8ba-214">Zarządzanie zabezpieczeniami obiektów blob</span><span class="sxs-lookup"><span data-stu-id="1d8ba-214">Managing security for blobs</span></span>

<span data-ttu-id="1d8ba-215">Domyślnie usługi Azure Storage chroni dane przez ograniczenie dostępu do właściciela konta, który znajduje się w posiadaniu klucze dostępu do konta.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-215">By default, Azure Storage keeps your data secure by limiting access to the account owner, who is in possession of the account access keys.</span></span> <span data-ttu-id="1d8ba-216">Potrzebne do udostępnienia danych obiektów blob na koncie magazynu, należy to zrobić bez uszczerbku dla bezpieczeństwa kluczy dostępu konta.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-216">When you need to share blob data in your storage account, it is important to do so without compromising the security of your account access keys.</span></span> <span data-ttu-id="1d8ba-217">Ponadto można zaszyfrować dane obiektu blob, aby zapewnić bezpieczeństwo podczas przesyłania przez sieć oraz w usłudze Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-217">Additionally, you can encrypt blob data to ensure that it is secure going over the wire and in Azure Storage.</span></span>

### <a name="controlling-access-to-blob-data"></a><span data-ttu-id="1d8ba-218">Kontrolowanie dostępu do danych obiektów blob</span><span class="sxs-lookup"><span data-stu-id="1d8ba-218">Controlling access to blob data</span></span>

<span data-ttu-id="1d8ba-219">Domyślnie dane obiektów blob na koncie magazynu jest dostępny tylko dla właściciela konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-219">By default, the blob data in your storage account is accessible only to storage account owner.</span></span> <span data-ttu-id="1d8ba-220">Uwierzytelniania żądań dotyczących magazynu obiektów Blob wymaga klucz dostępu do konta domyślnie.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-220">Authenticating requests against Blob storage requires the account access key by default.</span></span> <span data-ttu-id="1d8ba-221">Możesz jednak udostępnić określone dane obiektów blob innym użytkownikom.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-221">However, you might want to make certain blob data available to other users.</span></span>

<span data-ttu-id="1d8ba-222">Aby uzyskać więcej informacji na temat kontrolowania dostępu do magazynu obiektów blob, zobacz [przewodniku .NET dla sekcji magazynu obiektów blob w kontroli dostępu](/azure/storage/storage-dotnet-how-to-use-blobs#controlling-access-to-blob-data).</span><span class="sxs-lookup"><span data-stu-id="1d8ba-222">For details on how to control access to blob storage, see [the .NET guide for blob storage section on access control](/azure/storage/storage-dotnet-how-to-use-blobs#controlling-access-to-blob-data).</span></span>


### <a name="encrypting-blob-data"></a><span data-ttu-id="1d8ba-223">Szyfrowanie danych obiektów blob</span><span class="sxs-lookup"><span data-stu-id="1d8ba-223">Encrypting blob data</span></span>

<span data-ttu-id="1d8ba-224">Usługa Azure Storage obsługuje szyfrowanie danych obiektów blob zarówno po stronie klienta, jak i na serwerze.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-224">Azure Storage supports encrypting blob data both at the client and on the server.</span></span>

<span data-ttu-id="1d8ba-225">Aby uzyskać więcej informacji na temat szyfrowania danych obiektów blob, zobacz [.NET przewodnik dla sekcji magazynu obiektów blob w szyfrowania](/azure/storage/storage-dotnet-how-to-use-blobs#encrypting-blob-data).</span><span class="sxs-lookup"><span data-stu-id="1d8ba-225">For details on encrypting blob data, see [the .NET guide for blob storage section on encryption](/azure/storage/storage-dotnet-how-to-use-blobs#encrypting-blob-data).</span></span>

## <a name="next-steps"></a><span data-ttu-id="1d8ba-226">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="1d8ba-226">Next steps</span></span>

<span data-ttu-id="1d8ba-227">Teraz, kiedy znasz już podstawy magazynu obiektów Blob, skorzystaj z poniższych linków, aby dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-227">Now that you've learned the basics of Blob storage, follow these links to learn more.</span></span>

### <a name="tools"></a><span data-ttu-id="1d8ba-228">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="1d8ba-228">Tools</span></span>
- <span data-ttu-id="1d8ba-229">[F # AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/) F # typ dostawcy, który może służyć do eksplorowania zasobów obiektów Blob, tabel i kolejek usługi Azure Storage i łatwo zastosować operacji CRUD na nich.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-229">[F# AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/) An F# Type Provider which can be used to explore Blob, Table and Queue Azure Storage assets and easily apply CRUD operations on them.</span></span>
- <span data-ttu-id="1d8ba-230">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage) F # interfejsu API przy użyciu usługi Microsoft Azure Table Storage</span><span class="sxs-lookup"><span data-stu-id="1d8ba-230">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage) An F# API for using Microsoft Azure Table Storage service</span></span>
- <span data-ttu-id="1d8ba-231">[Microsoft Azure magazynu Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer) jest bezpłatna, aplikacja autonomiczny firmy Microsoft, który umożliwia pracę wizualnie z danymi usługi Azure Storage w systemie Windows, OS X i Linux.</span><span class="sxs-lookup"><span data-stu-id="1d8ba-231">[Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer) is a free, standalone app from Microsoft that enables you to work visually with Azure Storage data on Windows, OS X, and Linux.</span></span>

### <a name="blob-storage-reference"></a><span data-ttu-id="1d8ba-232">Odwołanie do obiektu blob magazynu</span><span class="sxs-lookup"><span data-stu-id="1d8ba-232">Blob storage reference</span></span>

- [<span data-ttu-id="1d8ba-233">Interfejsy API usługi Azure Storage dla platformy .NET</span><span class="sxs-lookup"><span data-stu-id="1d8ba-233">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="1d8ba-234">Dokumentacja interfejsu API REST usług magazynu Azure</span><span class="sxs-lookup"><span data-stu-id="1d8ba-234">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)

### <a name="related-guides"></a><span data-ttu-id="1d8ba-235">Przewodniki pokrewne</span><span class="sxs-lookup"><span data-stu-id="1d8ba-235">Related guides</span></span>

- [<span data-ttu-id="1d8ba-236">Wprowadzenie do magazynu obiektów Blob platformy Azure w języku C#</span><span class="sxs-lookup"><span data-stu-id="1d8ba-236">Getting Started with Azure Blob Storage in C#</span></span>](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/)
- [<span data-ttu-id="1d8ba-237">Transfer danych za pomocą wiersza polecenia azcopy w systemie Windows</span><span class="sxs-lookup"><span data-stu-id="1d8ba-237">Transfer data with the AzCopy command-line utility on Windows</span></span>](/azure/storage/common/storage-use-azcopy)
- [<span data-ttu-id="1d8ba-238">Transfer danych za pomocą wiersza polecenia azcopy w systemie Linux</span><span class="sxs-lookup"><span data-stu-id="1d8ba-238">Transfer data with the AzCopy command-line utility on Linux</span></span>](/azure/storage/common/storage-use-azcopy-linux)
- [<span data-ttu-id="1d8ba-239">Konfigurowanie parametrów połączenia usługi Azure Storage</span><span class="sxs-lookup"><span data-stu-id="1d8ba-239">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="1d8ba-240">Azure Storage Team Blog</span><span class="sxs-lookup"><span data-stu-id="1d8ba-240">Azure Storage Team Blog</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/)
