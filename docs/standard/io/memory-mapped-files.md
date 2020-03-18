---
title: Pliki mapowane w pamięci
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- memory-mapped files
- inter-process communication
ms.assetid: a483d1b5-64aa-45b6-86ef-11b859f7f02e
ms.openlocfilehash: 004da94bc7345bdc294562f0e1bedf6f1735adec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159718"
---
# <a name="memory-mapped-files"></a><span data-ttu-id="a5aa1-102">Pliki mapowane w pamięci</span><span class="sxs-lookup"><span data-stu-id="a5aa1-102">Memory-Mapped Files</span></span>
<span data-ttu-id="a5aa1-103">Plik mapowany w pamięci zawiera zawartość pliku w pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-103">A memory-mapped file contains the contents of a file in virtual memory.</span></span> <span data-ttu-id="a5aa1-104">To mapowanie między plikiem a przestrzenią pamięci umożliwia aplikacji, w tym wielu procesom, modyfikowanie pliku przez odczyt i zapis bezpośrednio w pamięci.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-104">This mapping between a file and memory space enables an application, including multiple processes, to modify the file by reading and writing directly to the memory.</span></span> <span data-ttu-id="a5aa1-105">Począwszy od .NET Framework 4, można użyć kodu zarządzanego, aby uzyskać dostęp do plików mapowanych w pamięci w taki sam sposób, jak natywne funkcje systemu Windows uzyskują dostęp do plików mapowanych w pamięci, zgodnie z opisem w [zarządzaniu plikami mapowanymi w pamięci](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="a5aa1-105">Starting with the .NET Framework 4, you can use managed code to access memory-mapped files in the same way that native Windows functions access memory-mapped files, as described in [Managing Memory-Mapped Files](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10)).</span></span>  
  
 <span data-ttu-id="a5aa1-106">Istnieją dwa typy plików mapowanych w pamięci:</span><span class="sxs-lookup"><span data-stu-id="a5aa1-106">There are two types of memory-mapped files:</span></span>  
  
- <span data-ttu-id="a5aa1-107">Utrwalione pliki mapowane w pamięci</span><span class="sxs-lookup"><span data-stu-id="a5aa1-107">Persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="a5aa1-108">Utrwalione pliki to pliki mapowane w pamięci, które są skojarzone z plikiem źródłowym na dysku.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-108">Persisted files are memory-mapped files that are associated with a source file on a disk.</span></span> <span data-ttu-id="a5aa1-109">Po zakończeniu ostatniego procesu pracy z plikiem dane są zapisywane w pliku źródłowym na dysku.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-109">When the last process has finished working with the file, the data is saved to the source file on the disk.</span></span> <span data-ttu-id="a5aa1-110">Te pliki mapowane w pamięci nadają się do pracy z bardzo dużymi plikami źródłowymi.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-110">These memory-mapped files are suitable for working with extremely large source files.</span></span>  
  
- <span data-ttu-id="a5aa1-111">Nieutrwaliwe pliki mapowane w pamięci</span><span class="sxs-lookup"><span data-stu-id="a5aa1-111">Non-persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="a5aa1-112">Pliki nieutrwalają się są plikami mapowanymi w pamięci, które nie są skojarzone z plikiem na dysku.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-112">Non-persisted files are memory-mapped files that are not associated with a file on a disk.</span></span> <span data-ttu-id="a5aa1-113">Po zakończeniu ostatniego procesu pracy z plikiem, dane zostaną utracone, a plik jest odzyskiwany przez wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-113">When the last process has finished working with the file, the data is lost and the file is reclaimed by garbage collection.</span></span> <span data-ttu-id="a5aa1-114">Pliki te są odpowiednie do tworzenia pamięci współużytkowanej dla komunikacji między procesami (IPC).</span><span class="sxs-lookup"><span data-stu-id="a5aa1-114">These files are suitable for creating shared memory for inter-process communications (IPC).</span></span>  
  
## <a name="processes-views-and-managing-memory"></a><span data-ttu-id="a5aa1-115">Procesy, widoki i zarządzanie pamięcią</span><span class="sxs-lookup"><span data-stu-id="a5aa1-115">Processes, Views, and Managing Memory</span></span>  
 <span data-ttu-id="a5aa1-116">Pliki mapowane w pamięci mogą być współużytkowane przez wiele procesów.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-116">Memory-mapped files can be shared across multiple processes.</span></span> <span data-ttu-id="a5aa1-117">Procesy można mapować do tego samego pliku mapowane pamięci przy użyciu nazwy wspólnej, który jest przypisany przez proces, który utworzył plik.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-117">Processes can map to the same memory-mapped file by using a common name that is assigned by the process that created the file.</span></span>  
  
 <span data-ttu-id="a5aa1-118">Aby pracować z plikiem mapowanym w pamięci, należy utworzyć widok całego pliku mapowanego w pamięci lub jego części.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-118">To work with a memory-mapped file, you must create a view of the entire memory-mapped file or a part of it.</span></span> <span data-ttu-id="a5aa1-119">Można również utworzyć wiele widoków do tej samej części pliku mapowane w pamięci, tworząc w ten sposób równoczesną pamięć.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-119">You can also create multiple views to the same part of the memory-mapped file, thereby creating concurrent memory.</span></span> <span data-ttu-id="a5aa1-120">Aby dwa widoki pozostały współbieżne, muszą zostać utworzone z tego samego pliku mapowanego w pamięci.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-120">For two views to remain concurrent, they have to be created from the same memory-mapped file.</span></span>  
  
 <span data-ttu-id="a5aa1-121">Wiele widoków może być również konieczne, jeśli plik jest większy niż rozmiar pamięci logicznej aplikacji dostępnej do mapowania pamięci (2 GB na komputerze 32-bitowym).</span><span class="sxs-lookup"><span data-stu-id="a5aa1-121">Multiple views may also be necessary if the file is greater than the size of the application’s logical memory space available for memory mapping (2 GB on a 32-bit computer).</span></span>  
  
 <span data-ttu-id="a5aa1-122">Istnieją dwa typy widoków: widok dostępu strumieniowego i widok dostępu losowego.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-122">There are two types of views: stream access view and random access view.</span></span> <span data-ttu-id="a5aa1-123">Użyj widoków dostępu strumieniowego, aby uzyskać sekwencyjne godowe; jest to zalecane w przypadku plików nieutrwalanych i IPC.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-123">Use stream access views for sequential access to a file; this is recommended for non-persisted files and IPC.</span></span> <span data-ttu-id="a5aa1-124">Widoki dostępu losowego są preferowane do pracy z utrwaonym pliki.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-124">Random access views are preferred for working with persisted files.</span></span>  
  
 <span data-ttu-id="a5aa1-125">Pliki mapowane w pamięci są dostępne za pośrednictwem menedżera pamięci systemu operacyjnego, więc plik jest automatycznie podzielony na partycje na kilka stron i dostępny w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-125">Memory-mapped files are accessed through the operating system’s memory manager, so the file is automatically partitioned into a number of pages and accessed as needed.</span></span> <span data-ttu-id="a5aa1-126">Nie musisz samodzielnie obsługiwać zarządzania pamięcią.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-126">You do not have to handle the memory management yourself.</span></span>  
  
 <span data-ttu-id="a5aa1-127">Na poniższej ilustracji pokazano, jak wiele procesów może mieć wiele nakładających się widoków do tego samego pliku mapowane w pamięci w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-127">The following illustration shows how multiple processes can have multiple and overlapping views to the same memory-mapped file at the same time.</span></span>

 <span data-ttu-id="a5aa1-128">Na poniższej ilustracji przedstawiono wiele i nakładanych widoków na plik mapowany w pamięci:</span><span class="sxs-lookup"><span data-stu-id="a5aa1-128">The following image shows multiple and overlapped views to a memory-mapped file:</span></span>  
  
 ![Zrzut ekranu przedstawiający widoki do pamięci&#45;zamapowany plik.](./media/memory-mapped-files/memory-map-persist-file.png)  
  
## <a name="programming-with-memory-mapped-files"></a><span data-ttu-id="a5aa1-130">Programowanie za pomocą plików mapowanych w pamięci</span><span class="sxs-lookup"><span data-stu-id="a5aa1-130">Programming with Memory-Mapped Files</span></span>  
 <span data-ttu-id="a5aa1-131">W poniższej tabeli przedstawiono przewodnik dotyczący używania obiektów plików mapowanych w pamięci i ich członków.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-131">The following table provides a guide for using memory-mapped file objects and their members.</span></span>  
  
|<span data-ttu-id="a5aa1-132">Zadanie</span><span class="sxs-lookup"><span data-stu-id="a5aa1-132">Task</span></span>|<span data-ttu-id="a5aa1-133">Metody lub właściwości do użycia</span><span class="sxs-lookup"><span data-stu-id="a5aa1-133">Methods or properties to use</span></span>|  
|----------|----------------------------------|  
|<span data-ttu-id="a5aa1-134">Aby uzyskać <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> obiekt, który reprezentuje utrwaliony plik mapowany z pamięci z pliku na dysku.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-134">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a persisted memory-mapped file from a file on disk.</span></span>|<span data-ttu-id="a5aa1-135"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>Metoda.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-135"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="a5aa1-136">Aby uzyskać <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> obiekt, który reprezentuje nieutrwaliwy plik mapowany w pamięci (nieskojarzony z plikiem na dysku).</span><span class="sxs-lookup"><span data-stu-id="a5aa1-136">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a non-persisted memory-mapped file (not associated with a file on disk).</span></span>|<span data-ttu-id="a5aa1-137"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>Metoda.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-137"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> method.</span></span><br /><br /> <span data-ttu-id="a5aa1-138">— lub —</span><span class="sxs-lookup"><span data-stu-id="a5aa1-138">- or -</span></span><br /><br /> <span data-ttu-id="a5aa1-139"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>Metoda.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-139"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="a5aa1-140">Aby uzyskać <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> obiekt istniejącego pliku mapowane jednych z pamięci (utrwalił lub nie utrwalił).</span><span class="sxs-lookup"><span data-stu-id="a5aa1-140">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object of an existing memory-mapped file (either persisted or non-persisted).</span></span>|<span data-ttu-id="a5aa1-141"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType>Metoda.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-141"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="a5aa1-142">Aby uzyskać <xref:System.IO.UnmanagedMemoryStream> obiekt dla sekwencyjnie dostępnego widoku do pliku mapowanego w pamięci.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-142">To obtain a <xref:System.IO.UnmanagedMemoryStream> object for a sequentially accessed view to the memory-mapped file.</span></span>|<span data-ttu-id="a5aa1-143"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType>Metoda.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-143"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="a5aa1-144">Aby uzyskać <xref:System.IO.UnmanagedMemoryAccessor> obiekt dla widoku dostępu losowego do fie mapowane pamięci.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-144">To obtain a <xref:System.IO.UnmanagedMemoryAccessor> object for a random access view to a memory-mapped fie.</span></span>|<span data-ttu-id="a5aa1-145"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType>Metoda.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-145"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="a5aa1-146">Aby uzyskać <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> obiekt do użycia z kodem niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-146">To obtain a <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> object to use with unmanaged code.</span></span>|<span data-ttu-id="a5aa1-147"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType>Właściwość.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-147"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="a5aa1-148">— lub —</span><span class="sxs-lookup"><span data-stu-id="a5aa1-148">- or -</span></span><br /><br /> <span data-ttu-id="a5aa1-149"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>Właściwość.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-149"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="a5aa1-150">— lub —</span><span class="sxs-lookup"><span data-stu-id="a5aa1-150">- or -</span></span><br /><br /> <span data-ttu-id="a5aa1-151"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>Właściwość.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-151"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span>|  
|<span data-ttu-id="a5aa1-152">Aby opóźnić przydzielanie pamięci do momentu utworzenia widoku (tylko pliki nieutrwaliwe).</span><span class="sxs-lookup"><span data-stu-id="a5aa1-152">To delay allocating memory until a view is created (non-persisted files only).</span></span><br /><br /> <span data-ttu-id="a5aa1-153">(Aby określić bieżący rozmiar strony <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> systemowej, należy użyć właściwości).</span><span class="sxs-lookup"><span data-stu-id="a5aa1-153">(To determine the current system page size, use the <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> property.)</span></span>|<span data-ttu-id="a5aa1-154"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A>metody z <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> wartością.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-154"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> method with the <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> value.</span></span><br /><br /> <span data-ttu-id="a5aa1-155">— lub —</span><span class="sxs-lookup"><span data-stu-id="a5aa1-155">- or -</span></span><br /><br /> <span data-ttu-id="a5aa1-156"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A>metody, które <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> mają wyliczenie jako parametr.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-156"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods that have a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> enumeration as a parameter.</span></span>|  
  
### <a name="security"></a><span data-ttu-id="a5aa1-157">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="a5aa1-157">Security</span></span>  
 <span data-ttu-id="a5aa1-158">Prawa dostępu można zastosować podczas tworzenia pliku mapowanego w pamięci, przy <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> użyciu następujących metod, które przyjmują wyliczenie jako parametr:</span><span class="sxs-lookup"><span data-stu-id="a5aa1-158">You can apply access rights when you create a memory-mapped file, by using the following methods that take a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> enumeration as a parameter:</span></span>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="a5aa1-159">Można określić prawa dostępu do otwierania istniejącego pliku <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> mapowane pamięci <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> przy użyciu metod, które przyjmują jako parametr.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-159">You can specify access rights for opening an existing memory-mapped file by using the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> methods that take an <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> as a parameter.</span></span>  
  
 <span data-ttu-id="a5aa1-160">Ponadto można dołączyć <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> obiekt, który zawiera wstępnie zdefiniowane reguły dostępu.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-160">In addition, you can include a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> object that contains predefined access rules.</span></span>  
  
 <span data-ttu-id="a5aa1-161">Aby zastosować nowe lub zmienione reguły dostępu do pliku <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> mapowanego w pamięci, użyj tej metody.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-161">To apply new or changed access rules to a memory-mapped file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> method.</span></span> <span data-ttu-id="a5aa1-162">Aby pobrać reguły dostępu lub inspekcji z <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> istniejącego pliku, użyj tej metody.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-162">To retrieve access or audit rules from an existing file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="a5aa1-163">Przykłady</span><span class="sxs-lookup"><span data-stu-id="a5aa1-163">Examples</span></span>  
  
### <a name="persisted-memory-mapped-files"></a><span data-ttu-id="a5aa1-164">Utrwalione pliki mapowane w pamięci</span><span class="sxs-lookup"><span data-stu-id="a5aa1-164">Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="a5aa1-165"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> Metody tworzą plik mapowany z pamięci z istniejącego pliku na dysku.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-165">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> methods create a memory-mapped file from an existing file on disk.</span></span>  
  
 <span data-ttu-id="a5aa1-166">Poniższy przykład tworzy mapowany w pamięci widok części bardzo dużego pliku i manipuluje jego częścią.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-166">The following example creates a memory-mapped view of a part of an extremely large file and manipulates a portion of it.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

 <span data-ttu-id="a5aa1-167">Poniższy przykład otwiera ten sam plik mapowany w pamięci dla innego procesu.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-167">The following example opens the same memory-mapped file for another process.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a><span data-ttu-id="a5aa1-168">Nieutrwaliwe pliki mapowane w pamięci</span><span class="sxs-lookup"><span data-stu-id="a5aa1-168">Non-Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="a5aa1-169">Metody <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> i tworzą plik mapowany w pamięci, który nie jest mapowany na istniejący plik na dysku.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-169">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> and <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods create a memory-mapped file that is not mapped to an existing file on disk.</span></span>  
  
 <span data-ttu-id="a5aa1-170">Poniższy przykład składa się z trzech oddzielnych procesów (aplikacji konsoli), które zapisują wartości logiczne do pliku mapowane go w pamięci.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-170">The following example consists of three separate processes (console applications) that write Boolean values to a memory-mapped file.</span></span> <span data-ttu-id="a5aa1-171">Występuje następująca sekwencja akcji:</span><span class="sxs-lookup"><span data-stu-id="a5aa1-171">The following sequence of actions occur:</span></span>  
  
1. <span data-ttu-id="a5aa1-172">`Process A`tworzy plik mapowany w pamięci i zapisuje w nim wartość.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-172">`Process A` creates the memory-mapped file and writes a value to it.</span></span>  
  
2. <span data-ttu-id="a5aa1-173">`Process B`otwiera plik mapowany w pamięci i zapisuje w nim wartość.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-173">`Process B` opens the memory-mapped file and writes a value to it.</span></span>  
  
3. <span data-ttu-id="a5aa1-174">`Process C`otwiera plik mapowany w pamięci i zapisuje w nim wartość.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-174">`Process C` opens the memory-mapped file and writes a value to it.</span></span>  
  
4. <span data-ttu-id="a5aa1-175">`Process A`odczytuje i wyświetla wartości z pliku mapowanego w pamięci.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-175">`Process A` reads and displays the values from the memory-mapped file.</span></span>  
  
5. <span data-ttu-id="a5aa1-176">Po `Process A` zakończeniu z pliku mapowane pamięci, plik jest natychmiast odzyskane przez wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-176">After `Process A` is finished with the memory-mapped file, the file is immediately reclaimed by garbage collection.</span></span>  
  
 <span data-ttu-id="a5aa1-177">Aby uruchomić ten przykład, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="a5aa1-177">To run this example, do the following:</span></span>  
  
1. <span data-ttu-id="a5aa1-178">Skompiluj aplikacje i otwórz trzy okna wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-178">Compile the applications and open three Command Prompt windows.</span></span>  
  
2. <span data-ttu-id="a5aa1-179">W pierwszym oknie wiersza `Process A`polecenia uruchom polecenie .</span><span class="sxs-lookup"><span data-stu-id="a5aa1-179">In the first Command Prompt window, run `Process A`.</span></span>  
  
3. <span data-ttu-id="a5aa1-180">W drugim oknie wiersza `Process B`polecenia uruchom polecenie .</span><span class="sxs-lookup"><span data-stu-id="a5aa1-180">In the second Command Prompt window, run `Process B`.</span></span>  
  
4. <span data-ttu-id="a5aa1-181">Wróć `Process A` do i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-181">Return to `Process A` and press ENTER.</span></span>  
  
5. <span data-ttu-id="a5aa1-182">W trzecim oknie wiersza `Process C`polecenia uruchom polecenie .</span><span class="sxs-lookup"><span data-stu-id="a5aa1-182">In the third Command Prompt window, run `Process C`.</span></span>  
  
6. <span data-ttu-id="a5aa1-183">Wróć `Process A` do i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="a5aa1-183">Return to `Process A` and press ENTER.</span></span>  
  
 <span data-ttu-id="a5aa1-184">Dane wyjściowe `Process A` są następujące:</span><span class="sxs-lookup"><span data-stu-id="a5aa1-184">The output of `Process A` is as follows:</span></span>  
  
```console  
Start Process B and press ENTER to continue.  
Start Process C and press ENTER to continue.  
Process A says: True  
Process B says: False  
Process C says: True  
```  
  
 <span data-ttu-id="a5aa1-185">**Proces A**</span><span class="sxs-lookup"><span data-stu-id="a5aa1-185">**Process A**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/vb/program.vb#1)]  
  
 <span data-ttu-id="a5aa1-186">**Proces B**</span><span class="sxs-lookup"><span data-stu-id="a5aa1-186">**Process B**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/vb/program.vb#1)]  
  
 <span data-ttu-id="a5aa1-187">**Proces C**</span><span class="sxs-lookup"><span data-stu-id="a5aa1-187">**Process C**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a5aa1-188">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5aa1-188">See also</span></span>

- [<span data-ttu-id="a5aa1-189">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="a5aa1-189">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
