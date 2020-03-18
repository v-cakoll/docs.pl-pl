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
# <a name="memory-mapped-files"></a>Pliki mapowane w pamięci
Plik mapowany w pamięci zawiera zawartość pliku w pamięci wirtualnej. To mapowanie między plikiem a przestrzenią pamięci umożliwia aplikacji, w tym wielu procesom, modyfikowanie pliku przez odczyt i zapis bezpośrednio w pamięci. Począwszy od .NET Framework 4, można użyć kodu zarządzanego, aby uzyskać dostęp do plików mapowanych w pamięci w taki sam sposób, jak natywne funkcje systemu Windows uzyskują dostęp do plików mapowanych w pamięci, zgodnie z opisem w [zarządzaniu plikami mapowanymi w pamięci](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10)).  
  
 Istnieją dwa typy plików mapowanych w pamięci:  
  
- Utrwalione pliki mapowane w pamięci  
  
     Utrwalione pliki to pliki mapowane w pamięci, które są skojarzone z plikiem źródłowym na dysku. Po zakończeniu ostatniego procesu pracy z plikiem dane są zapisywane w pliku źródłowym na dysku. Te pliki mapowane w pamięci nadają się do pracy z bardzo dużymi plikami źródłowymi.  
  
- Nieutrwaliwe pliki mapowane w pamięci  
  
     Pliki nieutrwalają się są plikami mapowanymi w pamięci, które nie są skojarzone z plikiem na dysku. Po zakończeniu ostatniego procesu pracy z plikiem, dane zostaną utracone, a plik jest odzyskiwany przez wyrzucanie elementów bezużytecznych. Pliki te są odpowiednie do tworzenia pamięci współużytkowanej dla komunikacji między procesami (IPC).  
  
## <a name="processes-views-and-managing-memory"></a>Procesy, widoki i zarządzanie pamięcią  
 Pliki mapowane w pamięci mogą być współużytkowane przez wiele procesów. Procesy można mapować do tego samego pliku mapowane pamięci przy użyciu nazwy wspólnej, który jest przypisany przez proces, który utworzył plik.  
  
 Aby pracować z plikiem mapowanym w pamięci, należy utworzyć widok całego pliku mapowanego w pamięci lub jego części. Można również utworzyć wiele widoków do tej samej części pliku mapowane w pamięci, tworząc w ten sposób równoczesną pamięć. Aby dwa widoki pozostały współbieżne, muszą zostać utworzone z tego samego pliku mapowanego w pamięci.  
  
 Wiele widoków może być również konieczne, jeśli plik jest większy niż rozmiar pamięci logicznej aplikacji dostępnej do mapowania pamięci (2 GB na komputerze 32-bitowym).  
  
 Istnieją dwa typy widoków: widok dostępu strumieniowego i widok dostępu losowego. Użyj widoków dostępu strumieniowego, aby uzyskać sekwencyjne godowe; jest to zalecane w przypadku plików nieutrwalanych i IPC. Widoki dostępu losowego są preferowane do pracy z utrwaonym pliki.  
  
 Pliki mapowane w pamięci są dostępne za pośrednictwem menedżera pamięci systemu operacyjnego, więc plik jest automatycznie podzielony na partycje na kilka stron i dostępny w razie potrzeby. Nie musisz samodzielnie obsługiwać zarządzania pamięcią.  
  
 Na poniższej ilustracji pokazano, jak wiele procesów może mieć wiele nakładających się widoków do tego samego pliku mapowane w pamięci w tym samym czasie.

 Na poniższej ilustracji przedstawiono wiele i nakładanych widoków na plik mapowany w pamięci:  
  
 ![Zrzut ekranu przedstawiający widoki do pamięci&#45;zamapowany plik.](./media/memory-mapped-files/memory-map-persist-file.png)  
  
## <a name="programming-with-memory-mapped-files"></a>Programowanie za pomocą plików mapowanych w pamięci  
 W poniższej tabeli przedstawiono przewodnik dotyczący używania obiektów plików mapowanych w pamięci i ich członków.  
  
|Zadanie|Metody lub właściwości do użycia|  
|----------|----------------------------------|  
|Aby uzyskać <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> obiekt, który reprezentuje utrwaliony plik mapowany z pamięci z pliku na dysku.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>Metoda.|  
|Aby uzyskać <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> obiekt, który reprezentuje nieutrwaliwy plik mapowany w pamięci (nieskojarzony z plikiem na dysku).|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>Metoda.<br /><br /> — lub —<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>Metoda.|  
|Aby uzyskać <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> obiekt istniejącego pliku mapowane jednych z pamięci (utrwalił lub nie utrwalił).|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType>Metoda.|  
|Aby uzyskać <xref:System.IO.UnmanagedMemoryStream> obiekt dla sekwencyjnie dostępnego widoku do pliku mapowanego w pamięci.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType>Metoda.|  
|Aby uzyskać <xref:System.IO.UnmanagedMemoryAccessor> obiekt dla widoku dostępu losowego do fie mapowane pamięci.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType>Metoda.|  
|Aby uzyskać <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> obiekt do użycia z kodem niezarządzanym.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType>Właściwość.<br /><br /> — lub —<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>Właściwość.<br /><br /> — lub —<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>Właściwość.|  
|Aby opóźnić przydzielanie pamięci do momentu utworzenia widoku (tylko pliki nieutrwaliwe).<br /><br /> (Aby określić bieżący rozmiar strony <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> systemowej, należy użyć właściwości).|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A>metody z <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> wartością.<br /><br /> — lub —<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A>metody, które <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> mają wyliczenie jako parametr.|  
  
### <a name="security"></a>Zabezpieczenia  
 Prawa dostępu można zastosować podczas tworzenia pliku mapowanego w pamięci, przy <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> użyciu następujących metod, które przyjmują wyliczenie jako parametr:  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 Można określić prawa dostępu do otwierania istniejącego pliku <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> mapowane pamięci <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> przy użyciu metod, które przyjmują jako parametr.  
  
 Ponadto można dołączyć <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> obiekt, który zawiera wstępnie zdefiniowane reguły dostępu.  
  
 Aby zastosować nowe lub zmienione reguły dostępu do pliku <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> mapowanego w pamięci, użyj tej metody. Aby pobrać reguły dostępu lub inspekcji z <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> istniejącego pliku, użyj tej metody.  
  
## <a name="examples"></a>Przykłady  
  
### <a name="persisted-memory-mapped-files"></a>Utrwalione pliki mapowane w pamięci  
 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> Metody tworzą plik mapowany z pamięci z istniejącego pliku na dysku.  
  
 Poniższy przykład tworzy mapowany w pamięci widok części bardzo dużego pliku i manipuluje jego częścią.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

 Poniższy przykład otwiera ten sam plik mapowany w pamięci dla innego procesu.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a>Nieutrwaliwe pliki mapowane w pamięci  
 Metody <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> i tworzą plik mapowany w pamięci, który nie jest mapowany na istniejący plik na dysku.  
  
 Poniższy przykład składa się z trzech oddzielnych procesów (aplikacji konsoli), które zapisują wartości logiczne do pliku mapowane go w pamięci. Występuje następująca sekwencja akcji:  
  
1. `Process A`tworzy plik mapowany w pamięci i zapisuje w nim wartość.  
  
2. `Process B`otwiera plik mapowany w pamięci i zapisuje w nim wartość.  
  
3. `Process C`otwiera plik mapowany w pamięci i zapisuje w nim wartość.  
  
4. `Process A`odczytuje i wyświetla wartości z pliku mapowanego w pamięci.  
  
5. Po `Process A` zakończeniu z pliku mapowane pamięci, plik jest natychmiast odzyskane przez wyrzucanie elementów bezużytecznych.  
  
 Aby uruchomić ten przykład, wykonaj następujące czynności:  
  
1. Skompiluj aplikacje i otwórz trzy okna wiersza polecenia.  
  
2. W pierwszym oknie wiersza `Process A`polecenia uruchom polecenie .  
  
3. W drugim oknie wiersza `Process B`polecenia uruchom polecenie .  
  
4. Wróć `Process A` do i naciśnij klawisz ENTER.  
  
5. W trzecim oknie wiersza `Process C`polecenia uruchom polecenie .  
  
6. Wróć `Process A` do i naciśnij klawisz ENTER.  
  
 Dane wyjściowe `Process A` są następujące:  
  
```console  
Start Process B and press ENTER to continue.  
Start Process C and press ENTER to continue.  
Process A says: True  
Process B says: False  
Process C says: True  
```  
  
 **Proces A**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/vb/program.vb#1)]  
  
 **Proces B**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/vb/program.vb#1)]  
  
 **Proces C**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/vb/program.vb#1)]  
  
## <a name="see-also"></a>Zobacz też

- [We/Wy plików i strumieni](../../../docs/standard/io/index.md)
