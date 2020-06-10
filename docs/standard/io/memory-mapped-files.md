---
title: Pliki mapowane w pamięci
description: Eksploruj pliki mapowane w pamięci w programie .NET, które zawierają zawartość pliku w pamięci wirtualnej, i Zezwalaj aplikacjom na modyfikowanie pliku przez zapis bezpośrednio do pamięci.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- memory-mapped files
- inter-process communication
ms.assetid: a483d1b5-64aa-45b6-86ef-11b859f7f02e
ms.openlocfilehash: db63c15357b0670c55b1174b91b02e2f49a0c4c1
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2020
ms.locfileid: "84661982"
---
# <a name="memory-mapped-files"></a><span data-ttu-id="17138-103">Pliki mapowane w pamięci</span><span class="sxs-lookup"><span data-stu-id="17138-103">Memory-Mapped Files</span></span>
<span data-ttu-id="17138-104">Plik mapowany w pamięci zawiera zawartość pliku w pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="17138-104">A memory-mapped file contains the contents of a file in virtual memory.</span></span> <span data-ttu-id="17138-105">To mapowanie między plikiem a miejscem pamięci umożliwia aplikacji, w tym wiele procesów, zmodyfikowanie pliku przez odczyt i zapis bezpośrednio do pamięci.</span><span class="sxs-lookup"><span data-stu-id="17138-105">This mapping between a file and memory space enables an application, including multiple processes, to modify the file by reading and writing directly to the memory.</span></span> <span data-ttu-id="17138-106">Począwszy od .NET Framework 4, można użyć kodu zarządzanego, aby uzyskać dostęp do plików mapowanych w pamięci w taki sam sposób, jak natywne funkcje systemu Windows uzyskują dostęp do plików mapowanych w pamięci, zgodnie z opisem w temacie [Zarządzanie plikami mapowanymi w pamięci](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="17138-106">Starting with the .NET Framework 4, you can use managed code to access memory-mapped files in the same way that native Windows functions access memory-mapped files, as described in [Managing Memory-Mapped Files](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10)).</span></span>  
  
 <span data-ttu-id="17138-107">Istnieją dwa typy plików mapowanych na pamięć:</span><span class="sxs-lookup"><span data-stu-id="17138-107">There are two types of memory-mapped files:</span></span>  
  
- <span data-ttu-id="17138-108">Utrwalone pliki mapowane w pamięci</span><span class="sxs-lookup"><span data-stu-id="17138-108">Persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="17138-109">Utrwalone pliki to pliki mapowane w pamięci, które są skojarzone z plikiem źródłowym na dysku.</span><span class="sxs-lookup"><span data-stu-id="17138-109">Persisted files are memory-mapped files that are associated with a source file on a disk.</span></span> <span data-ttu-id="17138-110">Gdy ostatni proces zakończył pracę z plikiem, dane są zapisywane w pliku źródłowym na dysku.</span><span class="sxs-lookup"><span data-stu-id="17138-110">When the last process has finished working with the file, the data is saved to the source file on the disk.</span></span> <span data-ttu-id="17138-111">Te pliki mapowane w pamięci są odpowiednie do pracy z bardzo dużymi plikami źródłowymi.</span><span class="sxs-lookup"><span data-stu-id="17138-111">These memory-mapped files are suitable for working with extremely large source files.</span></span>  
  
- <span data-ttu-id="17138-112">Nieutrwalone pliki mapowane w pamięci</span><span class="sxs-lookup"><span data-stu-id="17138-112">Non-persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="17138-113">Pliki nieutrwalone to pliki mapowane w pamięci, które nie są skojarzone z plikiem na dysku.</span><span class="sxs-lookup"><span data-stu-id="17138-113">Non-persisted files are memory-mapped files that are not associated with a file on a disk.</span></span> <span data-ttu-id="17138-114">Gdy ostatni proces zakończył pracę z plikiem, dane zostaną utracone i plik zostanie odczytany przez wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="17138-114">When the last process has finished working with the file, the data is lost and the file is reclaimed by garbage collection.</span></span> <span data-ttu-id="17138-115">Te pliki są odpowiednie do tworzenia pamięci współdzielonej dla komunikacji między procesami (IPC).</span><span class="sxs-lookup"><span data-stu-id="17138-115">These files are suitable for creating shared memory for inter-process communications (IPC).</span></span>  
  
## <a name="processes-views-and-managing-memory"></a><span data-ttu-id="17138-116">Procesy, widoki i zarządzanie pamięcią</span><span class="sxs-lookup"><span data-stu-id="17138-116">Processes, Views, and Managing Memory</span></span>  
 <span data-ttu-id="17138-117">Pliki mapowane w pamięci mogą być współużytkowane przez wiele procesów.</span><span class="sxs-lookup"><span data-stu-id="17138-117">Memory-mapped files can be shared across multiple processes.</span></span> <span data-ttu-id="17138-118">Procesy mogą mapować do tego samego pliku mapowanego na pamięć przy użyciu nazwy pospolitej przypisanej przez proces, który utworzył plik.</span><span class="sxs-lookup"><span data-stu-id="17138-118">Processes can map to the same memory-mapped file by using a common name that is assigned by the process that created the file.</span></span>  
  
 <span data-ttu-id="17138-119">Aby można było korzystać z pliku mapowanego na pamięć, należy utworzyć widok całego pliku mapowanego na pamięć lub jego części.</span><span class="sxs-lookup"><span data-stu-id="17138-119">To work with a memory-mapped file, you must create a view of the entire memory-mapped file or a part of it.</span></span> <span data-ttu-id="17138-120">Możesz również utworzyć wiele widoków w tej samej części pliku mapowanego na pamięć, tworząc współbieżną pamięć.</span><span class="sxs-lookup"><span data-stu-id="17138-120">You can also create multiple views to the same part of the memory-mapped file, thereby creating concurrent memory.</span></span> <span data-ttu-id="17138-121">Aby dwa widoki były pozostawać współbieżne, muszą zostać utworzone na podstawie tego samego pliku mapowanego na pamięć.</span><span class="sxs-lookup"><span data-stu-id="17138-121">For two views to remain concurrent, they have to be created from the same memory-mapped file.</span></span>  
  
 <span data-ttu-id="17138-122">Jeśli plik jest większy niż rozmiar przestrzeni pamięci logicznej aplikacji dostępnego dla mapowania pamięci (2 GB na komputerze 32-bitowym), może być również konieczne przeprowadzenie wielu widoków.</span><span class="sxs-lookup"><span data-stu-id="17138-122">Multiple views may also be necessary if the file is greater than the size of the application’s logical memory space available for memory mapping (2 GB on a 32-bit computer).</span></span>  
  
 <span data-ttu-id="17138-123">Istnieją dwa typy widoków: widok dostęp do strumienia i widok dostępu swobodnego.</span><span class="sxs-lookup"><span data-stu-id="17138-123">There are two types of views: stream access view and random access view.</span></span> <span data-ttu-id="17138-124">Użyj widoków dostępu do przesyłania strumieniowego, aby uzyskać sekwencyjny dostęp do pliku; jest to zalecane w przypadku plików nieutrwalonych i IPC.</span><span class="sxs-lookup"><span data-stu-id="17138-124">Use stream access views for sequential access to a file; this is recommended for non-persisted files and IPC.</span></span> <span data-ttu-id="17138-125">Widoki dostępu losowego są preferowane w pracy z utrwalonymi plikami.</span><span class="sxs-lookup"><span data-stu-id="17138-125">Random access views are preferred for working with persisted files.</span></span>  
  
 <span data-ttu-id="17138-126">Pliki mapowane w pamięci są dostępne za pomocą Menedżera pamięci systemu operacyjnego, więc plik jest automatycznie podzielony na kilka stron i dostępne w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="17138-126">Memory-mapped files are accessed through the operating system’s memory manager, so the file is automatically partitioned into a number of pages and accessed as needed.</span></span> <span data-ttu-id="17138-127">Zarządzanie pamięcią nie jest konieczne.</span><span class="sxs-lookup"><span data-stu-id="17138-127">You do not have to handle the memory management yourself.</span></span>  
  
 <span data-ttu-id="17138-128">Na poniższej ilustracji przedstawiono, jak wiele procesów może mieć wiele i nakładających się widoków do tego samego pliku mapowanego w pamięci w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="17138-128">The following illustration shows how multiple processes can have multiple and overlapping views to the same memory-mapped file at the same time.</span></span>

 <span data-ttu-id="17138-129">Na poniższej ilustracji przedstawiono wiele i nakładające się widoki do pliku mapowanego na pamięć:</span><span class="sxs-lookup"><span data-stu-id="17138-129">The following image shows multiple and overlapped views to a memory-mapped file:</span></span>  
  
 ![Zrzut ekranu pokazujący widoki w pamięci&#45;mapowany plik.](./media/memory-mapped-files/memory-map-persist-file.png)  
  
## <a name="programming-with-memory-mapped-files"></a><span data-ttu-id="17138-131">Programowanie przy użyciu plików mapowanych na pamięć</span><span class="sxs-lookup"><span data-stu-id="17138-131">Programming with Memory-Mapped Files</span></span>  
 <span data-ttu-id="17138-132">W poniższej tabeli przedstawiono Przewodnik po użyciu obiektów plików mapowanych na pamięć i ich członków.</span><span class="sxs-lookup"><span data-stu-id="17138-132">The following table provides a guide for using memory-mapped file objects and their members.</span></span>  
  
|<span data-ttu-id="17138-133">Zadanie</span><span class="sxs-lookup"><span data-stu-id="17138-133">Task</span></span>|<span data-ttu-id="17138-134">Metody lub właściwości do użycia</span><span class="sxs-lookup"><span data-stu-id="17138-134">Methods or properties to use</span></span>|  
|----------|----------------------------------|  
|<span data-ttu-id="17138-135">Aby uzyskać <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> obiekt, który reprezentuje utrwalony plik mapowany w pamięci z pliku na dysku.</span><span class="sxs-lookup"><span data-stu-id="17138-135">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a persisted memory-mapped file from a file on disk.</span></span>|<span data-ttu-id="17138-136"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>Method.</span><span class="sxs-lookup"><span data-stu-id="17138-136"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="17138-137">Aby uzyskać <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> obiekt, który reprezentuje nieutrwalony plik mapowany na pamięć (nieskojarzony z plikiem na dysku).</span><span class="sxs-lookup"><span data-stu-id="17138-137">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a non-persisted memory-mapped file (not associated with a file on disk).</span></span>|<span data-ttu-id="17138-138"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>Method.</span><span class="sxs-lookup"><span data-stu-id="17138-138"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> method.</span></span><br /><br /> <span data-ttu-id="17138-139">— lub —</span><span class="sxs-lookup"><span data-stu-id="17138-139">- or -</span></span><br /><br /> <span data-ttu-id="17138-140"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>Method.</span><span class="sxs-lookup"><span data-stu-id="17138-140"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="17138-141">Aby uzyskać <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> obiekt istniejącego pliku mapowanego na pamięć (utrwalone lub nieutrwalone).</span><span class="sxs-lookup"><span data-stu-id="17138-141">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object of an existing memory-mapped file (either persisted or non-persisted).</span></span>|<span data-ttu-id="17138-142"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType>Method.</span><span class="sxs-lookup"><span data-stu-id="17138-142"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="17138-143">Uzyskanie obiektu do <xref:System.IO.UnmanagedMemoryStream> widoku z sekwencyjnym dostępem do pliku mapowanego na pamięć.</span><span class="sxs-lookup"><span data-stu-id="17138-143">To obtain a <xref:System.IO.UnmanagedMemoryStream> object for a sequentially accessed view to the memory-mapped file.</span></span>|<span data-ttu-id="17138-144"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType>Method.</span><span class="sxs-lookup"><span data-stu-id="17138-144"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="17138-145">Aby uzyskać <xref:System.IO.UnmanagedMemoryAccessor> obiekt dla widoku dostępu losowego do pole mapowanego na pamięć.</span><span class="sxs-lookup"><span data-stu-id="17138-145">To obtain a <xref:System.IO.UnmanagedMemoryAccessor> object for a random access view to a memory-mapped fie.</span></span>|<span data-ttu-id="17138-146"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType>Method.</span><span class="sxs-lookup"><span data-stu-id="17138-146"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="17138-147">Aby uzyskać <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> obiekt do użycia z niezarządzanym kodem.</span><span class="sxs-lookup"><span data-stu-id="17138-147">To obtain a <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> object to use with unmanaged code.</span></span>|<span data-ttu-id="17138-148"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType>wartość.</span><span class="sxs-lookup"><span data-stu-id="17138-148"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="17138-149">— lub —</span><span class="sxs-lookup"><span data-stu-id="17138-149">- or -</span></span><br /><br /> <span data-ttu-id="17138-150"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>wartość.</span><span class="sxs-lookup"><span data-stu-id="17138-150"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="17138-151">— lub —</span><span class="sxs-lookup"><span data-stu-id="17138-151">- or -</span></span><br /><br /> <span data-ttu-id="17138-152"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>wartość.</span><span class="sxs-lookup"><span data-stu-id="17138-152"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span>|  
|<span data-ttu-id="17138-153">Aby opóźnić przydzielanie pamięci do momentu utworzenia widoku (tylko pliki nieutrwalone).</span><span class="sxs-lookup"><span data-stu-id="17138-153">To delay allocating memory until a view is created (non-persisted files only).</span></span><br /><br /> <span data-ttu-id="17138-154">(Aby określić bieżący rozmiar strony systemowej, użyj <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> Właściwości).</span><span class="sxs-lookup"><span data-stu-id="17138-154">(To determine the current system page size, use the <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> property.)</span></span>|<span data-ttu-id="17138-155"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A>Metoda z <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> wartością.</span><span class="sxs-lookup"><span data-stu-id="17138-155"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> method with the <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> value.</span></span><br /><br /> <span data-ttu-id="17138-156">— lub —</span><span class="sxs-lookup"><span data-stu-id="17138-156">- or -</span></span><br /><br /> <span data-ttu-id="17138-157"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A>metody, które mają <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> Wyliczenie jako parametr.</span><span class="sxs-lookup"><span data-stu-id="17138-157"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods that have a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> enumeration as a parameter.</span></span>|  
  
### <a name="security"></a><span data-ttu-id="17138-158">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="17138-158">Security</span></span>  
 <span data-ttu-id="17138-159">Prawa dostępu można stosować podczas tworzenia pliku mapowanego na pamięć przy użyciu następujących metod, które pobierają <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> Wyliczenie jako parametr:</span><span class="sxs-lookup"><span data-stu-id="17138-159">You can apply access rights when you create a memory-mapped file, by using the following methods that take a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> enumeration as a parameter:</span></span>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="17138-160">Możesz określić prawa dostępu do otwierania istniejącego pliku mapowanego na pamięć przy użyciu <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> metod, które przyjmują <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> jako parametr.</span><span class="sxs-lookup"><span data-stu-id="17138-160">You can specify access rights for opening an existing memory-mapped file by using the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> methods that take an <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> as a parameter.</span></span>  
  
 <span data-ttu-id="17138-161">Ponadto można dołączyć <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> obiekt, który zawiera wstępnie zdefiniowane reguły dostępu.</span><span class="sxs-lookup"><span data-stu-id="17138-161">In addition, you can include a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> object that contains predefined access rules.</span></span>  
  
 <span data-ttu-id="17138-162">Aby zastosować nowe lub zmienione reguły dostępu do pliku mapowanego na pamięć, użyj <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="17138-162">To apply new or changed access rules to a memory-mapped file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> method.</span></span> <span data-ttu-id="17138-163">Aby pobrać reguły dostępu lub inspekcji z istniejącego pliku, należy użyć <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="17138-163">To retrieve access or audit rules from an existing file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="17138-164">Przykłady</span><span class="sxs-lookup"><span data-stu-id="17138-164">Examples</span></span>  
  
### <a name="persisted-memory-mapped-files"></a><span data-ttu-id="17138-165">Utrwalone pliki mapowane w pamięci</span><span class="sxs-lookup"><span data-stu-id="17138-165">Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="17138-166"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A>Metody tworzą plik mapowany w pamięci z istniejącego pliku na dysku.</span><span class="sxs-lookup"><span data-stu-id="17138-166">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> methods create a memory-mapped file from an existing file on disk.</span></span>  
  
 <span data-ttu-id="17138-167">Poniższy przykład tworzy widok mapowany w pamięci części bardzo dużego pliku i operuje na jego części.</span><span class="sxs-lookup"><span data-stu-id="17138-167">The following example creates a memory-mapped view of a part of an extremely large file and manipulates a portion of it.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

 <span data-ttu-id="17138-168">Poniższy przykład powoduje otwarcie tego samego pliku mapowanego na pamięć dla innego procesu.</span><span class="sxs-lookup"><span data-stu-id="17138-168">The following example opens the same memory-mapped file for another process.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a><span data-ttu-id="17138-169">Nieutrwalone pliki mapowane w pamięci</span><span class="sxs-lookup"><span data-stu-id="17138-169">Non-Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="17138-170"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A>Metody i <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> tworzą plik mapowany w pamięci, który nie jest mapowany na istniejący plik na dysku.</span><span class="sxs-lookup"><span data-stu-id="17138-170">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> and <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods create a memory-mapped file that is not mapped to an existing file on disk.</span></span>  
  
 <span data-ttu-id="17138-171">Poniższy przykład składa się z trzech oddzielnych procesów (aplikacji konsolowych), które zapisują wartości logiczne do pliku mapowanego na pamięć.</span><span class="sxs-lookup"><span data-stu-id="17138-171">The following example consists of three separate processes (console applications) that write Boolean values to a memory-mapped file.</span></span> <span data-ttu-id="17138-172">Występuje następująca sekwencja akcji:</span><span class="sxs-lookup"><span data-stu-id="17138-172">The following sequence of actions occur:</span></span>  
  
1. <span data-ttu-id="17138-173">`Process A`tworzy plik mapowany w pamięci i zapisuje w nim wartość.</span><span class="sxs-lookup"><span data-stu-id="17138-173">`Process A` creates the memory-mapped file and writes a value to it.</span></span>  
  
2. <span data-ttu-id="17138-174">`Process B`otwiera plik mapowany w pamięci i zapisuje w nim wartość.</span><span class="sxs-lookup"><span data-stu-id="17138-174">`Process B` opens the memory-mapped file and writes a value to it.</span></span>  
  
3. <span data-ttu-id="17138-175">`Process C`otwiera plik mapowany w pamięci i zapisuje w nim wartość.</span><span class="sxs-lookup"><span data-stu-id="17138-175">`Process C` opens the memory-mapped file and writes a value to it.</span></span>  
  
4. <span data-ttu-id="17138-176">`Process A`odczytuje i wyświetla wartości z pliku mapowanego w pamięci.</span><span class="sxs-lookup"><span data-stu-id="17138-176">`Process A` reads and displays the values from the memory-mapped file.</span></span>  
  
5. <span data-ttu-id="17138-177">Po `Process A` zakończeniu przy użyciu pliku mapowanego na pamięć plik zostanie natychmiast odczytany przez wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="17138-177">After `Process A` is finished with the memory-mapped file, the file is immediately reclaimed by garbage collection.</span></span>  
  
 <span data-ttu-id="17138-178">Aby uruchomić ten przykład, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="17138-178">To run this example, do the following:</span></span>  
  
1. <span data-ttu-id="17138-179">Skompiluj aplikacje i otwórz trzy okna wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="17138-179">Compile the applications and open three Command Prompt windows.</span></span>  
  
2. <span data-ttu-id="17138-180">W pierwszym oknie wiersza polecenia Uruchom polecenie `Process A` .</span><span class="sxs-lookup"><span data-stu-id="17138-180">In the first Command Prompt window, run `Process A`.</span></span>  
  
3. <span data-ttu-id="17138-181">W drugim oknie wiersza polecenia Uruchom polecenie `Process B` .</span><span class="sxs-lookup"><span data-stu-id="17138-181">In the second Command Prompt window, run `Process B`.</span></span>  
  
4. <span data-ttu-id="17138-182">Wróć do `Process A` i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="17138-182">Return to `Process A` and press ENTER.</span></span>  
  
5. <span data-ttu-id="17138-183">W trzecim oknie wiersza polecenia Uruchom polecenie `Process C` .</span><span class="sxs-lookup"><span data-stu-id="17138-183">In the third Command Prompt window, run `Process C`.</span></span>  
  
6. <span data-ttu-id="17138-184">Wróć do `Process A` i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="17138-184">Return to `Process A` and press ENTER.</span></span>  
  
 <span data-ttu-id="17138-185">Dane wyjściowe `Process A` są następujące:</span><span class="sxs-lookup"><span data-stu-id="17138-185">The output of `Process A` is as follows:</span></span>  
  
```console  
Start Process B and press ENTER to continue.  
Start Process C and press ENTER to continue.  
Process A says: True  
Process B says: False  
Process C says: True  
```  
  
 <span data-ttu-id="17138-186">**Przetwarzaj A**</span><span class="sxs-lookup"><span data-stu-id="17138-186">**Process A**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/vb/program.vb#1)]  
  
 <span data-ttu-id="17138-187">**Proces B**</span><span class="sxs-lookup"><span data-stu-id="17138-187">**Process B**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/vb/program.vb#1)]  
  
 <span data-ttu-id="17138-188">**Proces C**</span><span class="sxs-lookup"><span data-stu-id="17138-188">**Process C**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="17138-189">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="17138-189">See also</span></span>

- [<span data-ttu-id="17138-190">We/wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="17138-190">File and Stream I/O</span></span>](index.md)
