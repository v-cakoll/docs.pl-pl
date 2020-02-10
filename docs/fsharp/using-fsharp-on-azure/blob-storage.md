---
title: Rozpoczynanie pracy z usługą Azure Blob Storage przy użyciu języka F#
description: Przechowuj dane niestrukturalne w chmurze za pomocą usługi Azure Blob Storage.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 79f6a559ac603b0544916764126a988d3f3f43d7
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092632"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a><span data-ttu-id="59183-103">Rozpoczynanie pracy z usługą Azure Blob Storage za pomocą języka F\#</span><span class="sxs-lookup"><span data-stu-id="59183-103">Get started with Azure Blob storage using F\#</span></span>

<span data-ttu-id="59183-104">Magazyn obiektów blob Azure jest usługą służącą do przechowywania danych niestrukturalnych w chmurze w postaci obiektów blob.</span><span class="sxs-lookup"><span data-stu-id="59183-104">Azure Blob storage is a service that stores unstructured data in the cloud as objects/blobs.</span></span> <span data-ttu-id="59183-105">Magazyn obiektów blob umożliwia przechowywanie dowolnego typu danych tekstowych lub binarnych, takich jak dokumenty, pliki multimedialne lub instalatory aplikacji.</span><span class="sxs-lookup"><span data-stu-id="59183-105">Blob storage can store any type of text or binary data, such as a document, media file, or application installer.</span></span> <span data-ttu-id="59183-106">Magazyn obiektów blob jest również nazywany magazynem obiektów.</span><span class="sxs-lookup"><span data-stu-id="59183-106">Blob storage is also referred to as object storage.</span></span>

<span data-ttu-id="59183-107">W tym artykule przedstawiono sposób wykonywania typowych zadań za pomocą usługi BLOB Storage.</span><span class="sxs-lookup"><span data-stu-id="59183-107">This article shows you how to perform common tasks using Blob storage.</span></span> <span data-ttu-id="59183-108">Przykłady są zapisywane przy użyciu F# biblioteki klienckiej usługi Azure Storage dla platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="59183-108">The samples are written using F# using the Azure Storage Client Library for .NET.</span></span> <span data-ttu-id="59183-109">Objęte zadaniami obejmują sposób przekazywania, wyświetlania, pobierania i usuwania obiektów BLOB.</span><span class="sxs-lookup"><span data-stu-id="59183-109">The tasks covered include how to upload, list, download, and delete blobs.</span></span>

<span data-ttu-id="59183-110">Ogólne omówienie usługi BLOB Storage można znaleźć [w przewodniku .NET dla usługi BLOB Storage](/azure/storage/blobs/storage-quickstart-blobs-dotnet).</span><span class="sxs-lookup"><span data-stu-id="59183-110">For a conceptual overview of blob storage, see [the .NET guide for blob storage](/azure/storage/blobs/storage-quickstart-blobs-dotnet).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="59183-111">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="59183-111">Prerequisites</span></span>

<span data-ttu-id="59183-112">Aby skorzystać z tego przewodnika, musisz najpierw [utworzyć konto usługi Azure Storage](/azure/storage/common/storage-account-create).</span><span class="sxs-lookup"><span data-stu-id="59183-112">To use this guide, you must first [create an Azure storage account](/azure/storage/common/storage-account-create).</span></span> <span data-ttu-id="59183-113">Wymagany jest również klucz dostępu do magazynu dla tego konta.</span><span class="sxs-lookup"><span data-stu-id="59183-113">You also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="59183-114">Utwórz F# skrypt i uruchom F# interaktywny</span><span class="sxs-lookup"><span data-stu-id="59183-114">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="59183-115">Przykłady w tym artykule mogą być używane w F# aplikacji lub F# skrypcie.</span><span class="sxs-lookup"><span data-stu-id="59183-115">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="59183-116">Aby utworzyć F# skrypt, Utwórz plik z rozszerzeniem `.fsx`, na przykład `blobs.fsx`, w środowisku F# deweloperskim.</span><span class="sxs-lookup"><span data-stu-id="59183-116">To create an F# script, create a file with the `.fsx` extension, for example `blobs.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="59183-117">Następnie użyj [Menedżera pakietów](package-management.md) , takiego jak [Paket](https://fsprojects.github.io/Paket/) lub [NuGet](https://www.nuget.org/) , aby zainstalować `WindowsAzure.Storage` i `Microsoft.WindowsAzure.ConfigurationManager` pakiety oraz `WindowsAzure.Storage.dll` odwołania i `Microsoft.WindowsAzure.Configuration.dll` w skrypcie przy użyciu dyrektywy `#r`.</span><span class="sxs-lookup"><span data-stu-id="59183-117">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` and `Microsoft.WindowsAzure.ConfigurationManager` packages and reference `WindowsAzure.Storage.dll` and `Microsoft.WindowsAzure.Configuration.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="59183-118">Dodawanie deklaracji przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="59183-118">Add namespace declarations</span></span>

<span data-ttu-id="59183-119">Dodaj następujące instrukcje `open` na początku pliku `blobs.fsx`:</span><span class="sxs-lookup"><span data-stu-id="59183-119">Add the following `open` statements to the top of the `blobs.fsx` file:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="59183-120">Pobieranie parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="59183-120">Get your connection string</span></span>

<span data-ttu-id="59183-121">Potrzebujesz parametrów połączenia usługi Azure Storage dla tego samouczka.</span><span class="sxs-lookup"><span data-stu-id="59183-121">You need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="59183-122">Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz [Konfigurowanie parametrów połączenia magazynu](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="59183-122">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="59183-123">W samouczku wprowadzono parametry połączenia w skrypcie, takie jak:</span><span class="sxs-lookup"><span data-stu-id="59183-123">For the tutorial, you enter your connection string in your script, like this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

<span data-ttu-id="59183-124">Nie jest to jednak **zalecane** w przypadku rzeczywistych projektów.</span><span class="sxs-lookup"><span data-stu-id="59183-124">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="59183-125">Klucz konta magazynu jest podobny do hasła głównego konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="59183-125">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="59183-126">Zawsze chroń klucz konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="59183-126">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="59183-127">Nie udostępniaj go innym użytkownikom, nie koduj go trwale ani nie zapisuj w zwykłym pliku tekstowym, do którego mają dostęp inne osoby.</span><span class="sxs-lookup"><span data-stu-id="59183-127">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="59183-128">Możesz ponownie wygenerować klucz za pomocą witryny Azure Portal, jeśli uważasz, że jego zabezpieczenia mogły zostać naruszone.</span><span class="sxs-lookup"><span data-stu-id="59183-128">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="59183-129">W przypadku prawdziwych aplikacji najlepszym sposobem obsługi parametrów połączenia magazynu jest w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="59183-129">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="59183-130">Aby pobrać parametry połączenia z pliku konfiguracji, można to zrobić:</span><span class="sxs-lookup"><span data-stu-id="59183-130">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

<span data-ttu-id="59183-131">Użycie programu Azure Configuration Manager jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="59183-131">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="59183-132">Można również użyć interfejsu API, takiego jak typ `ConfigurationManager` .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="59183-132">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="59183-133">Analizowanie parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="59183-133">Parse the connection string</span></span>

<span data-ttu-id="59183-134">Aby przeanalizować parametry połączenia, użyj:</span><span class="sxs-lookup"><span data-stu-id="59183-134">To parse the connection string, use:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

<span data-ttu-id="59183-135">Spowoduje to zwrócenie `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="59183-135">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-some-local-dummy-data"></a><span data-ttu-id="59183-136">Tworzenie niektórych lokalnych danych fikcyjnych</span><span class="sxs-lookup"><span data-stu-id="59183-136">Create some local dummy data</span></span>

<span data-ttu-id="59183-137">Przed rozpoczęciem Utwórz własne fikcyjne dane lokalne w katalogu naszego skryptu.</span><span class="sxs-lookup"><span data-stu-id="59183-137">Before you begin, create some dummy local data in the directory of our script.</span></span> <span data-ttu-id="59183-138">Później przekażesz te dane.</span><span class="sxs-lookup"><span data-stu-id="59183-138">Later you upload this data.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a><span data-ttu-id="59183-139">Tworzenie klienta usługi Blob</span><span class="sxs-lookup"><span data-stu-id="59183-139">Create the Blob service client</span></span>

<span data-ttu-id="59183-140">Typ `CloudBlobClient` umożliwia pobieranie kontenerów i obiektów BLOB przechowywanych w usłudze BLOB Storage.</span><span class="sxs-lookup"><span data-stu-id="59183-140">The `CloudBlobClient` type enables you to retrieve containers and blobs stored in Blob storage.</span></span> <span data-ttu-id="59183-141">Oto jeden ze sposobów tworzenia klienta usługi:</span><span class="sxs-lookup"><span data-stu-id="59183-141">Here's one way to create the service client:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

<span data-ttu-id="59183-142">Teraz możesz przystąpić do pisania kodu, który będzie odczytywać dane z Magazynu obiektów blob i zapisywać je w nim.</span><span class="sxs-lookup"><span data-stu-id="59183-142">Now you are ready to write code that reads data from and writes data to Blob storage.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="59183-143">Tworzenie kontenera</span><span class="sxs-lookup"><span data-stu-id="59183-143">Create a container</span></span>

<span data-ttu-id="59183-144">W tym przykładzie pokazano, jak utworzyć kontener, jeśli jeszcze nie istnieje:</span><span class="sxs-lookup"><span data-stu-id="59183-144">This example shows how to create a container if it does not already exist:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

<span data-ttu-id="59183-145">Domyślnie nowy kontener jest prywatny, co oznacza, że musisz podać klucz dostępu do magazynu, aby pobierać obiekty blob z tego kontenera.</span><span class="sxs-lookup"><span data-stu-id="59183-145">By default, the new container is private, meaning that you must specify your storage access key to download blobs from this container.</span></span> <span data-ttu-id="59183-146">Jeśli chcesz, aby pliki w kontenerze były dostępne dla wszystkich, możesz ustawić kontener jako publiczny przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="59183-146">If you want to make the files within the container available to everyone, you can set the container to be public using the following code:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

<span data-ttu-id="59183-147">Wszyscy użytkownicy Internetu mogą wyświetlać obiekty blob w kontenerze publicznym, ale można je modyfikować lub usuwać tylko przy użyciu odpowiedniego klucza dostępu do konta lub sygnatury dostępu współdzielonego.</span><span class="sxs-lookup"><span data-stu-id="59183-147">Anyone on the Internet can see blobs in a public container, but you can modify or delete them only if you have the appropriate account access key or a shared access signature.</span></span>

## <a name="upload-a-blob-into-a-container"></a><span data-ttu-id="59183-148">Przekazywanie obiektu blob do kontenera</span><span class="sxs-lookup"><span data-stu-id="59183-148">Upload a blob into a container</span></span>

<span data-ttu-id="59183-149">Azure Blob Storage obsługuje blokowe i stronicowe obiekty blob.</span><span class="sxs-lookup"><span data-stu-id="59183-149">Azure Blob Storage supports block blobs and page blobs.</span></span> <span data-ttu-id="59183-150">W większości przypadków zalecanym typem jest blokowy obiekt BLOB.</span><span class="sxs-lookup"><span data-stu-id="59183-150">In most cases, a block blob is the recommended type to use.</span></span>

<span data-ttu-id="59183-151">Aby przekazać plik do blokowego obiektu blob, pobierz odwołanie do kontenera i uzyskaj za jego pomocą odwołanie do blokowego obiektu blob.</span><span class="sxs-lookup"><span data-stu-id="59183-151">To upload a file to a block blob, get a container reference and use it to get a block blob reference.</span></span> <span data-ttu-id="59183-152">Po uzyskaniu odwołania do obiektu BLOB możesz przekazać do niego dowolny strumień danych, wywołując metodę `UploadFromFile`.</span><span class="sxs-lookup"><span data-stu-id="59183-152">Once you have a blob reference, you can upload any stream of data to it by calling the `UploadFromFile` method.</span></span> <span data-ttu-id="59183-153">Ta operacja tworzy obiekt BLOB, jeśli jeszcze nie istnieje, lub go zastępuje, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="59183-153">This operation creates the blob if it didn't previously exist, or overwrite it if it does exist.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a><span data-ttu-id="59183-154">Wyświetlanie listy obiektów blob w kontenerze</span><span class="sxs-lookup"><span data-stu-id="59183-154">List the blobs in a container</span></span>

<span data-ttu-id="59183-155">Aby wyświetlić listę obiektów blob w kontenerze, należy najpierw uzyskać odwołanie do kontenera.</span><span class="sxs-lookup"><span data-stu-id="59183-155">To list the blobs in a container, first get a container reference.</span></span> <span data-ttu-id="59183-156">Następnie można użyć metody `ListBlobs` kontenera do pobrania obiektów blob i/lub znajdujących się w niej katalogów.</span><span class="sxs-lookup"><span data-stu-id="59183-156">You can then use the container's `ListBlobs` method to retrieve the blobs and/or directories within it.</span></span> <span data-ttu-id="59183-157">Aby uzyskać dostęp do bogatego zestawu właściwości i metod dla zwracanych `IListBlobItem`, należy rzutować go do `CloudBlockBlob`, `CloudPageBlob`lub `CloudBlobDirectory` obiektu.</span><span class="sxs-lookup"><span data-stu-id="59183-157">To access the rich set of properties and methods for a returned `IListBlobItem`, you must cast it to a `CloudBlockBlob`, `CloudPageBlob`, or `CloudBlobDirectory` object.</span></span> <span data-ttu-id="59183-158">Jeśli typ jest nieznany, można zastosować sprawdzanie typu, aby określić, do którego obiektu rzutować obiekt.</span><span class="sxs-lookup"><span data-stu-id="59183-158">If the type is unknown, you can use a type check to determine which to cast it to.</span></span> <span data-ttu-id="59183-159">Poniższy kod przedstawia sposób pobierania i zwracania identyfikatora URI poszczególnych elementów w kontenerze `mydata`:</span><span class="sxs-lookup"><span data-stu-id="59183-159">The following code demonstrates how to retrieve and output the URI of each item in the `mydata` container:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

<span data-ttu-id="59183-160">Można także nazywać obiekty blob z informacjami o ścieżce w ich nazwach.</span><span class="sxs-lookup"><span data-stu-id="59183-160">You can also name blobs with path information in their names.</span></span> <span data-ttu-id="59183-161">Powoduje to utworzenie wirtualnej struktury katalogów, które można organizować i przechodzić między nimi tak jak w przypadku tradycyjnego systemu plików.</span><span class="sxs-lookup"><span data-stu-id="59183-161">This creates a virtual directory structure that you can organize and traverse as you would a traditional file system.</span></span> <span data-ttu-id="59183-162">Należy pamiętać, że struktura katalogów jest wyłącznie wirtualna — jedyne zasoby dostępne w Magazynie obiektów blob to kontenery i obiekty blob.</span><span class="sxs-lookup"><span data-stu-id="59183-162">Note that the directory structure is virtual only - the only resources available in Blob storage are containers and blobs.</span></span> <span data-ttu-id="59183-163">Jednak Biblioteka klienta magazynu oferuje `CloudBlobDirectory` obiektu do odwoływania się do katalogu wirtualnego i upraszcza proces pracy z obiektami BLOB zorganizowanymi w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="59183-163">However, the storage client library offers a `CloudBlobDirectory` object to refer to a virtual directory and simplify the process of working with blobs that are organized in this way.</span></span>

<span data-ttu-id="59183-164">Rozważmy na przykład następujący zestaw blokowych obiektów blob w kontenerze o nazwie `photos`:</span><span class="sxs-lookup"><span data-stu-id="59183-164">For example, consider the following set of block blobs in a container named `photos`:</span></span>

<span data-ttu-id="59183-165">*Photo1. jpg*</span><span class="sxs-lookup"><span data-stu-id="59183-165">*photo1.jpg*</span></span>\
<span data-ttu-id="59183-166">*2015/Architecture/Description. txt*</span><span class="sxs-lookup"><span data-stu-id="59183-166">*2015/architecture/description.txt*</span></span>\
<span data-ttu-id="59183-167">*2015/photo3. jpg*</span><span class="sxs-lookup"><span data-stu-id="59183-167">*2015/architecture/photo3.jpg*</span></span>\
<span data-ttu-id="59183-168">*2015/photo4. jpg*</span><span class="sxs-lookup"><span data-stu-id="59183-168">*2015/architecture/photo4.jpg*</span></span>\
<span data-ttu-id="59183-169">*2016/Architecture/photo5. jpg*</span><span class="sxs-lookup"><span data-stu-id="59183-169">*2016/architecture/photo5.jpg*</span></span>\
<span data-ttu-id="59183-170">*2016/Architecture/photo6. jpg*</span><span class="sxs-lookup"><span data-stu-id="59183-170">*2016/architecture/photo6.jpg*</span></span>\
<span data-ttu-id="59183-171">*2016/Architecture/Description. txt*</span><span class="sxs-lookup"><span data-stu-id="59183-171">*2016/architecture/description.txt*</span></span>\
<span data-ttu-id="59183-172">*2016/photo7. jpg*</span><span class="sxs-lookup"><span data-stu-id="59183-172">*2016/photo7.jpg*</span></span>\

<span data-ttu-id="59183-173">Gdy wywołasz `ListBlobs` w kontenerze (jak w powyższym przykładzie), zwracana jest lista hierarchiczna.</span><span class="sxs-lookup"><span data-stu-id="59183-173">When you call `ListBlobs` on a container (as in the above sample), a hierarchical listing is returned.</span></span> <span data-ttu-id="59183-174">Jeśli zawiera zarówno obiekty `CloudBlobDirectory`, jak i `CloudBlockBlob`, reprezentujące katalogi i obiektów BLOB w kontenerze, a następnie wynikowe wyniki wyglądają podobnie do tego:</span><span class="sxs-lookup"><span data-stu-id="59183-174">If it contains both `CloudBlobDirectory` and `CloudBlockBlob` objects, representing the directories and blobs in the container, respectively, then the resulting output looks similar to this:</span></span>

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

<span data-ttu-id="59183-175">Opcjonalnie można ustawić parametr `UseFlatBlobListing` metody `ListBlobs`, aby `true`.</span><span class="sxs-lookup"><span data-stu-id="59183-175">Optionally, you can set the `UseFlatBlobListing` parameter of the `ListBlobs` method to `true`.</span></span> <span data-ttu-id="59183-176">W takim przypadku każdy obiekt BLOB w kontenerze jest zwracany jako obiekt `CloudBlockBlob`.</span><span class="sxs-lookup"><span data-stu-id="59183-176">In this case, every blob in the container is returned as a `CloudBlockBlob` object.</span></span> <span data-ttu-id="59183-177">Wywołanie `ListBlobs`, aby zwrócić płaską listę, wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="59183-177">The call to `ListBlobs` to return a flat listing looks like this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

<span data-ttu-id="59183-178">w zależności od bieżącej zawartości kontenera wyniki wyglądają następująco:</span><span class="sxs-lookup"><span data-stu-id="59183-178">and, depending on the current contents of your container, the results look like this:</span></span>

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

## <a name="download-blobs"></a><span data-ttu-id="59183-179">Pobieranie obiektów blob</span><span class="sxs-lookup"><span data-stu-id="59183-179">Download blobs</span></span>

<span data-ttu-id="59183-180">Aby pobrać obiekty blob, najpierw Pobierz odwołanie do obiektu BLOB, a następnie Wywołaj metodę `DownloadToStream`.</span><span class="sxs-lookup"><span data-stu-id="59183-180">To download blobs, first retrieve a blob reference and then call the `DownloadToStream` method.</span></span> <span data-ttu-id="59183-181">W poniższym przykładzie zastosowano metodę `DownloadToStream`, aby przesłać zawartość obiektu BLOB do obiektu strumienia, który można następnie zachować do pliku lokalnego.</span><span class="sxs-lookup"><span data-stu-id="59183-181">The following example uses the `DownloadToStream` method to transfer the blob contents to a stream object that you can then persist to a local file.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

<span data-ttu-id="59183-182">Możesz również użyć metody `DownloadToStream`, aby pobrać zawartość obiektu BLOB jako ciąg tekstowy.</span><span class="sxs-lookup"><span data-stu-id="59183-182">You can also use the `DownloadToStream` method to download the contents of a blob as a text string.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a><span data-ttu-id="59183-183">Usuwanie obiektów blob</span><span class="sxs-lookup"><span data-stu-id="59183-183">Delete blobs</span></span>

<span data-ttu-id="59183-184">Aby usunąć obiekt BLOB, należy najpierw pobrać odwołanie do obiektu BLOB, a następnie wywołać metodę `Delete`.</span><span class="sxs-lookup"><span data-stu-id="59183-184">To delete a blob, first get a blob reference and then call the `Delete` method on it.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a><span data-ttu-id="59183-185">Asynchroniczne wyświetlanie obiektów blob na stronach</span><span class="sxs-lookup"><span data-stu-id="59183-185">List blobs in pages asynchronously</span></span>

<span data-ttu-id="59183-186">Jeśli chcesz wyświetlić dużą liczbę obiektów blob lub kontrolować liczbę wyników zwracanych przez jedną operację wyświetlania listy, możesz wyświetlić obiekty blob na stronach wyników.</span><span class="sxs-lookup"><span data-stu-id="59183-186">If you are listing a large number of blobs, or you want to control the number of results you return in one listing operation, you can list blobs in pages of results.</span></span> <span data-ttu-id="59183-187">W tym przykładzie przedstawiono sposób asynchronicznego zwracania wyników na stronach, dzięki czemu wykonanie nie jest blokowane podczas oczekiwania na zwrócenie dużych zestawów wyników.</span><span class="sxs-lookup"><span data-stu-id="59183-187">This example shows how to return results in pages asynchronously, so that execution is not blocked while waiting to return a large set of results.</span></span>

<span data-ttu-id="59183-188">Ten przykład pokazuje płaską listę obiektów blob, ale można również wykonać listę hierarchiczną, ustawiając parametr `useFlatBlobListing` metody `ListBlobsSegmentedAsync`, aby `false`.</span><span class="sxs-lookup"><span data-stu-id="59183-188">This example shows a flat blob listing, but you can also perform a hierarchical listing, by setting the `useFlatBlobListing` parameter of the `ListBlobsSegmentedAsync` method to `false`.</span></span>

<span data-ttu-id="59183-189">Przykład definiuje metodę asynchroniczną przy użyciu bloku `async`.</span><span class="sxs-lookup"><span data-stu-id="59183-189">The sample defines an asynchronous method, using an `async` block.</span></span> <span data-ttu-id="59183-190">Słowo kluczowe ``let!`` wstrzymuje wykonywanie przykładowej metody do momentu zakończenia zadania tworzenia listy.</span><span class="sxs-lookup"><span data-stu-id="59183-190">The ``let!`` keyword suspends execution of the sample method until the listing task completes.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

<span data-ttu-id="59183-191">Teraz można użyć tej procedury asynchronicznej w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="59183-191">We can now use this asynchronous routine as follows.</span></span> <span data-ttu-id="59183-192">Najpierw przekażesz niektóre fikcyjne dane (przy użyciu pliku lokalnego utworzonego wcześniej w tym samouczku).</span><span class="sxs-lookup"><span data-stu-id="59183-192">First you upload some dummy data (using the local file created earlier in this tutorial).</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

<span data-ttu-id="59183-193">Teraz Wywołaj procedurę.</span><span class="sxs-lookup"><span data-stu-id="59183-193">Now, call the routine.</span></span> <span data-ttu-id="59183-194">Użyj `Async.RunSynchronously`, aby wymusić wykonanie operacji asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="59183-194">You use `Async.RunSynchronously` to force the execution of the asynchronous operation.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a><span data-ttu-id="59183-195">Zapisywanie do uzupełnialnego obiektu blob</span><span class="sxs-lookup"><span data-stu-id="59183-195">Writing to an append blob</span></span>

<span data-ttu-id="59183-196">Uzupełnialny obiekt blob jest zoptymalizowany pod kątem operacji dołączania, takich jak rejestrowanie.</span><span class="sxs-lookup"><span data-stu-id="59183-196">An append blob is optimized for append operations, such as logging.</span></span> <span data-ttu-id="59183-197">Podobnie jak blokowy obiekt blob, uzupełnialny obiekt blob jest złożony z bloków, ale nowy blok dodany do uzupełnialnego obiektu blob jest zawsze dołączany na końcu obiektu blob.</span><span class="sxs-lookup"><span data-stu-id="59183-197">Like a block blob, an append blob is comprised of blocks, but when you add a new block to an append blob, it is always appended to the end of the blob.</span></span> <span data-ttu-id="59183-198">Nie można zaktualizować lub usunąć istniejącego bloku w uzupełnialnym obiekcie blob.</span><span class="sxs-lookup"><span data-stu-id="59183-198">You cannot update or delete an existing block in an append blob.</span></span> <span data-ttu-id="59183-199">Identyfikatory bloków w uzupełnialnym obiekcie blob nie są widoczne, jak w przypadku blokowego obiektu blob.</span><span class="sxs-lookup"><span data-stu-id="59183-199">The block IDs for an append blob are not exposed as they are for a block blob.</span></span>

<span data-ttu-id="59183-200">Każdy blok w uzupełnialnym obiekcie blob może różnić się rozmiarem, który może wynosić maksymalnie 4 MB, a uzupełnialny obiekt blob może zawierać do 50 000 bloków.</span><span class="sxs-lookup"><span data-stu-id="59183-200">Each block in an append blob can be a different size, up to a maximum of 4 MB, and an append blob can include a maximum of 50,000 blocks.</span></span> <span data-ttu-id="59183-201">Z tego względu maksymalny rozmiar uzupełnialnego obiektu blob nieznacznie przekracza 195 GB (4 MB X 50 000 bloków).</span><span class="sxs-lookup"><span data-stu-id="59183-201">The maximum size of an append blob is therefore slightly more than 195 GB (4 MB X 50,000 blocks).</span></span>

<span data-ttu-id="59183-202">Poniższy przykład tworzy nowy obiekt BLOB dołączania i dołącza do niego pewne dane, symulując prostą operację rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="59183-202">The following example creates a new append blob and appends some data to it, simulating a simple logging operation.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

<span data-ttu-id="59183-203">Aby uzyskać więcej informacji o różnicach między tymi trzema typami obiektów blob, zobacz [Understanding Block Blobs, Page Blobs, and Append Blobs](https://msdn.microsoft.com/library/azure/ee691964.aspx) (Omówienie blokowych i stronicowych obiektów blob oraz uzupełnialnych obiektów blob).</span><span class="sxs-lookup"><span data-stu-id="59183-203">See [Understanding Block Blobs, Page Blobs, and Append Blobs](https://msdn.microsoft.com/library/azure/ee691964.aspx) for more information about the differences between the three types of blobs.</span></span>

## <a name="concurrent-access"></a><span data-ttu-id="59183-204">Dostęp współbieżny</span><span class="sxs-lookup"><span data-stu-id="59183-204">Concurrent access</span></span>

<span data-ttu-id="59183-205">Aby zapewnić obsługę współbieżnego dostępu do obiektu BLOB z wielu klientów lub wielu wystąpień procesów, można użyć elementów **ETags** lub **leases**.</span><span class="sxs-lookup"><span data-stu-id="59183-205">To support concurrent access to a blob from multiple clients or multiple process instances, you can use **ETags** or **leases**.</span></span>

- <span data-ttu-id="59183-206">**ETag** — umożliwia wykrycie, że obiekt BLOB lub kontener został zmodyfikowany przez inny proces</span><span class="sxs-lookup"><span data-stu-id="59183-206">**Etag** - provides a way to detect that the blob or container has been modified by another process</span></span>

- <span data-ttu-id="59183-207">**Dzierżawa** — umożliwia uzyskanie dostępu do obiektu BLOB z wyłącznym, odnawialnym, zapisem lub usunięciem w danym okresie czasu</span><span class="sxs-lookup"><span data-stu-id="59183-207">**Lease** - provides a way to obtain exclusive, renewable, write or delete access to a blob for a period of time</span></span>

<span data-ttu-id="59183-208">Aby uzyskać więcej informacji, zobacz [Zarządzanie współbieżnością w Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span><span class="sxs-lookup"><span data-stu-id="59183-208">For more information, see [Managing Concurrency in Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span></span>

## <a name="naming-containers"></a><span data-ttu-id="59183-209">Nazywanie kontenerów</span><span class="sxs-lookup"><span data-stu-id="59183-209">Naming containers</span></span>

<span data-ttu-id="59183-210">Każdy obiekt blob w usłudze Azure Storage musi znajdować się w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="59183-210">Every blob in Azure storage must reside in a container.</span></span> <span data-ttu-id="59183-211">Kontener jest częścią nazwy obiektu blob.</span><span class="sxs-lookup"><span data-stu-id="59183-211">The container forms part of the blob name.</span></span> <span data-ttu-id="59183-212">Na przykład `mydata` to nazwa kontenera w następujących przykładowych identyfikatorach URI obiektów blob:</span><span class="sxs-lookup"><span data-stu-id="59183-212">For example, `mydata` is the name of the container in these sample blob URIs:</span></span>

- `https://storagesample.blob.core.windows.net/mydata/blob1.txt`
- `https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg`

<span data-ttu-id="59183-213">Nazwa kontenera musi być prawidłową nazwą DNS zgodną z następującymi zasadami nazewnictwa:</span><span class="sxs-lookup"><span data-stu-id="59183-213">A container name must be a valid DNS name, conforming to the following naming rules:</span></span>

1. <span data-ttu-id="59183-214">Nazwa kontenera musi zaczynać się literą lub cyfrą i może zawierać tylko litery, cyfry i znak kreski (-).</span><span class="sxs-lookup"><span data-stu-id="59183-214">Container names must start with a letter or number, and can contain only letters, numbers, and the dash (-) character.</span></span>
1. <span data-ttu-id="59183-215">Bezpośrednio przed każdym znakiem kreski (-) i bezpośrednio po nim musi występować litera lub cyfra. W nazwach kontenerów następujące po sobie kreski są niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="59183-215">Every dash (-) character must be immediately preceded and followed by a letter or number; consecutive dashes are not permitted in container names.</span></span>
1. <span data-ttu-id="59183-216">Wszystkie litery w nazwie kontenera muszą być małymi literami.</span><span class="sxs-lookup"><span data-stu-id="59183-216">All letters in a container name must be lowercase.</span></span>
1. <span data-ttu-id="59183-217">Nazwy kontenerów muszą zawierać od 3 do 63 znaków.</span><span class="sxs-lookup"><span data-stu-id="59183-217">Container names must be from 3 through 63 characters long.</span></span>

<span data-ttu-id="59183-218">Należy pamiętać, że nazwa kontenera może zawierać tylko małe litery.</span><span class="sxs-lookup"><span data-stu-id="59183-218">Note that the name of a container must always be lowercase.</span></span> <span data-ttu-id="59183-219">Jeśli w nazwie kontenera wystąpi wielka litera lub reguły nazewnictwa dotyczące kontenerów zostaną naruszone w inny sposób, może zostać wyświetlony błąd 400 (Nieprawidłowe żądanie).</span><span class="sxs-lookup"><span data-stu-id="59183-219">If you include an upper-case letter in a container name, or otherwise violate the container naming rules, you may receive a 400 error (Bad Request).</span></span>

## <a name="managing-security-for-blobs"></a><span data-ttu-id="59183-220">Zarządzanie zabezpieczeniami obiektów blob</span><span class="sxs-lookup"><span data-stu-id="59183-220">Managing security for blobs</span></span>

<span data-ttu-id="59183-221">Domyślnie usługa Azure Storage chroni dane, umożliwiając dostęp wyłącznie właścicielowi konta, który ma klucze dostępu do konta.</span><span class="sxs-lookup"><span data-stu-id="59183-221">By default, Azure Storage keeps your data secure by limiting access to the account owner, who is in possession of the account access keys.</span></span> <span data-ttu-id="59183-222">W przypadku potrzeby udostępnienia danych obiektów blob na koncie magazynu ważne jest, aby zrobić to bez uszczerbku dla bezpieczeństwa kluczy dostępu do konta.</span><span class="sxs-lookup"><span data-stu-id="59183-222">When you need to share blob data in your storage account, it is important to do so without compromising the security of your account access keys.</span></span> <span data-ttu-id="59183-223">Dodatkowo można zaszyfrować dane obiektu blob, aby zapewnić ich bezpieczeństwo podczas przesyłania przez sieć oraz w usłudze Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="59183-223">Additionally, you can encrypt blob data to ensure that it is secure going over the wire and in Azure Storage.</span></span>

### <a name="controlling-access-to-blob-data"></a><span data-ttu-id="59183-224">Kontrolowanie dostępu do danych obiektów blob</span><span class="sxs-lookup"><span data-stu-id="59183-224">Controlling access to blob data</span></span>

<span data-ttu-id="59183-225">Domyślnie dane obiektów blob na koncie magazynu są dostępne tylko dla właściciela konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="59183-225">By default, the blob data in your storage account is accessible only to storage account owner.</span></span> <span data-ttu-id="59183-226">Domyślnie do uwierzytelniania żądań dotyczących Magazynu obiektów blob jest wymagany klucz dostępu do konta.</span><span class="sxs-lookup"><span data-stu-id="59183-226">Authenticating requests against Blob storage requires the account access key by default.</span></span> <span data-ttu-id="59183-227">Jednak może być konieczne udostępnienie pewnych danych obiektów BLOB innym użytkownikom.</span><span class="sxs-lookup"><span data-stu-id="59183-227">However, you might want to make certain blob data available to other users.</span></span>

### <a name="encrypting-blob-data"></a><span data-ttu-id="59183-228">Szyfrowanie danych obiektów blob</span><span class="sxs-lookup"><span data-stu-id="59183-228">Encrypting blob data</span></span>

<span data-ttu-id="59183-229">Usługa Azure Storage obsługuje szyfrowanie danych obiektów BLOB zarówno na kliencie, jak i na serwerze.</span><span class="sxs-lookup"><span data-stu-id="59183-229">Azure Storage supports encrypting blob data both at the client and on the server.</span></span>

## <a name="next-steps"></a><span data-ttu-id="59183-230">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="59183-230">Next steps</span></span>

<span data-ttu-id="59183-231">Teraz, kiedy znasz już podstawy usługi Blob Storage, skorzystaj z poniższych linków, aby dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="59183-231">Now that you've learned the basics of Blob storage, follow these links to learn more.</span></span>

### <a name="tools"></a><span data-ttu-id="59183-232">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="59183-232">Tools</span></span>

- <span data-ttu-id="59183-233">[ F# AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)</span><span class="sxs-lookup"><span data-stu-id="59183-233">[F# AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)</span></span>\
<span data-ttu-id="59183-234">Dostawca F# typów, który może służyć do eksplorowania obiektów blob, tabel i kolejek zasobów usługi Azure Storage oraz łatwego zastosowania na nich CRUD operacji.</span><span class="sxs-lookup"><span data-stu-id="59183-234">An F# Type Provider which can be used to explore Blob, Table and Queue Azure Storage assets and easily apply CRUD operations on them.</span></span>

- <span data-ttu-id="59183-235">[FSharp. Azure. Storage](https://github.com/fsprojects/FSharp.Azure.Storage)</span><span class="sxs-lookup"><span data-stu-id="59183-235">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage)</span></span>\
<span data-ttu-id="59183-236">F# Interfejs API służący do korzystania z usługi Microsoft Azure Table Storage</span><span class="sxs-lookup"><span data-stu-id="59183-236">An F# API for using Microsoft Azure Table Storage service</span></span>

- <span data-ttu-id="59183-237">[Eksplorator usługi Microsoft Azure Storage (darmową)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)</span><span class="sxs-lookup"><span data-stu-id="59183-237">[Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)</span></span>\
<span data-ttu-id="59183-238">Bezpłatna, autonomiczna aplikacja oferowana przez firmę Microsoft, która umożliwia wizualne korzystanie z danych usługi Azure Storage w systemach Windows, OS X i Linux.</span><span class="sxs-lookup"><span data-stu-id="59183-238">A free, standalone app from Microsoft that enables you to work visually with Azure Storage data on Windows, OS X, and Linux.</span></span>

### <a name="blob-storage-reference"></a><span data-ttu-id="59183-239">Informacje o usłudze Blob Storage</span><span class="sxs-lookup"><span data-stu-id="59183-239">Blob storage reference</span></span>

- [<span data-ttu-id="59183-240">Interfejsy API usługi Azure Storage dla platformy .NET</span><span class="sxs-lookup"><span data-stu-id="59183-240">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="59183-241">Dokumentacja interfejsu API REST usługi Azure Storage</span><span class="sxs-lookup"><span data-stu-id="59183-241">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/)

### <a name="related-guides"></a><span data-ttu-id="59183-242">Pokrewne prowadnice</span><span class="sxs-lookup"><span data-stu-id="59183-242">Related guides</span></span>

- [<span data-ttu-id="59183-243">Przykłady Blob Storage platformy Azure dla platformy .NET</span><span class="sxs-lookup"><span data-stu-id="59183-243">Azure Blob Storage Samples for .NET</span></span>](https://docs.microsoft.com/samples/azure-samples/storage-blob-dotnet-getting-started/storage-blob-dotnet-getting-started/)
- [<span data-ttu-id="59183-244">Wprowadzenie do AzCopy</span><span class="sxs-lookup"><span data-stu-id="59183-244">Get started with AzCopy</span></span>](/azure/storage/common/storage-use-azcopy-v10)
- [<span data-ttu-id="59183-245">Konfiguracja parametrów połączenia usługi Azure Storage</span><span class="sxs-lookup"><span data-stu-id="59183-245">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="59183-246">Blog zespołu odpowiedzialnego za usługę Azure Storage</span><span class="sxs-lookup"><span data-stu-id="59183-246">Azure Storage Team Blog</span></span>](https://docs.microsoft.com/archive/blogs/windowsazurestorage/)
- [<span data-ttu-id="59183-247">Szybki Start: korzystanie z platformy .NET do tworzenia obiektów BLOB w magazynie obiektów</span><span class="sxs-lookup"><span data-stu-id="59183-247">Quickstart: Use .NET to create a blob in object storage</span></span>](/azure/storage/blobs/storage-quickstart-blobs-dotnet)
