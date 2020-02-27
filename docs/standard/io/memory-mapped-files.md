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
ms.openlocfilehash: 7d80099fcfcba58cd863004ba7faf0bafa3abd09
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628023"
---
# <a name="memory-mapped-files"></a>Pliki mapowane w pamięci
Plik mapowany w pamięci zawiera zawartość pliku w pamięci wirtualnej. To mapowanie między plikiem a miejscem pamięci umożliwia aplikacji, w tym wiele procesów, zmodyfikowanie pliku przez odczyt i zapis bezpośrednio do pamięci. Począwszy od .NET Framework 4, można użyć kodu zarządzanego, aby uzyskać dostęp do plików mapowanych w pamięci w taki sam sposób, jak natywne funkcje systemu Windows uzyskują dostęp do plików mapowanych w pamięci, zgodnie z opisem w temacie [Zarządzanie plikami mapowanymi w pamięci](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10)).  
  
 Istnieją dwa typy plików mapowanych na pamięć:  
  
- Utrwalone pliki mapowane w pamięci  
  
     Utrwalone pliki to pliki mapowane w pamięci, które są skojarzone z plikiem źródłowym na dysku. Gdy ostatni proces zakończył pracę z plikiem, dane są zapisywane w pliku źródłowym na dysku. Te pliki mapowane w pamięci są odpowiednie do pracy z bardzo dużymi plikami źródłowymi.  
  
- Nieutrwalone pliki mapowane w pamięci  
  
     Pliki nieutrwalone to pliki mapowane w pamięci, które nie są skojarzone z plikiem na dysku. Gdy ostatni proces zakończył pracę z plikiem, dane zostaną utracone i plik zostanie odczytany przez wyrzucanie elementów bezużytecznych. Te pliki są odpowiednie do tworzenia pamięci współdzielonej dla komunikacji między procesami (IPC).  
  
## <a name="processes-views-and-managing-memory"></a>Procesy, widoki i zarządzanie pamięcią  
 Pliki mapowane w pamięci mogą być współużytkowane przez wiele procesów. Procesy mogą mapować do tego samego pliku mapowanego na pamięć przy użyciu nazwy pospolitej przypisanej przez proces, który utworzył plik.  
  
 Aby można było korzystać z pliku mapowanego na pamięć, należy utworzyć widok całego pliku mapowanego na pamięć lub jego części. Możesz również utworzyć wiele widoków w tej samej części pliku mapowanego na pamięć, tworząc współbieżną pamięć. Aby dwa widoki były pozostawać współbieżne, muszą zostać utworzone na podstawie tego samego pliku mapowanego na pamięć.  
  
 Jeśli plik jest większy niż rozmiar przestrzeni pamięci logicznej aplikacji dostępnego dla mapowania pamięci (2 GB na komputerze 32-bitowym), może być również konieczne przeprowadzenie wielu widoków.  
  
 Istnieją dwa typy widoków: widok dostęp do strumienia i widok dostępu swobodnego. Użyj widoków dostępu do przesyłania strumieniowego, aby uzyskać sekwencyjny dostęp do pliku; jest to zalecane w przypadku plików nieutrwalonych i IPC. Widoki dostępu losowego są preferowane w pracy z utrwalonymi plikami.  
  
 Pliki mapowane w pamięci są dostępne za pomocą Menedżera pamięci systemu operacyjnego, więc plik jest automatycznie podzielony na kilka stron i dostępne w razie potrzeby. Zarządzanie pamięcią nie jest konieczne.  
  
 Na poniższej ilustracji przedstawiono, jak wiele procesów może mieć wiele i nakładających się widoków do tego samego pliku mapowanego w pamięci w tym samym czasie.

 Na poniższej ilustracji przedstawiono wiele i nakładające się widoki do pliku mapowanego na pamięć:  
  
 ![Zrzut ekranu pokazujący widoki do pliku&#45;mapowanego na pamięć.](./media/memory-mapped-files/memory-map-persist-file.png)  
  
## <a name="programming-with-memory-mapped-files"></a>Programowanie przy użyciu plików mapowanych na pamięć  
 W poniższej tabeli przedstawiono Przewodnik po użyciu obiektów plików mapowanych na pamięć i ich członków.  
  
|Zadanie|Metody lub właściwości do użycia|  
|----------|----------------------------------|  
|Aby uzyskać <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> obiekt, który reprezentuje utrwalony plik mapowany w pamięci z pliku na dysku.|Metoda <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>.|  
|Aby uzyskać <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> obiekt, który reprezentuje nieutrwalony plik mapowany na pamięć (nieskojarzony z plikiem na dysku).|Metoda <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>.<br /><br /> oraz<br /><br /> Metoda <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>.|  
|Aby uzyskać <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> obiekt istniejący plik mapowany w pamięci (utrwalony lub nieutrwalony).|Metoda <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType>.|  
|Aby uzyskać <xref:System.IO.UnmanagedMemoryStream> obiektu do widoku z sekwencyjnym dostępem do pliku mapowanego na pamięć.|Metoda <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType>.|  
|Aby uzyskać <xref:System.IO.UnmanagedMemoryAccessor> obiektu na potrzeby widoku dostępu losowego do pole mapowanych na pamięć.|Metoda <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType>.|  
|Aby uzyskać <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> obiektu do użycia z niezarządzanym kodem.|Właściwość <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType>.<br /><br /> oraz<br /><br /> Właściwość <xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>.<br /><br /> oraz<br /><br /> Właściwość <xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>.|  
|Aby opóźnić przydzielanie pamięci do momentu utworzenia widoku (tylko pliki nieutrwalone).<br /><br /> (Aby określić bieżący rozmiar strony systemowej, użyj właściwości <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType>).|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> metodę z wartością <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType>.<br /><br /> oraz<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> metod, które mają <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> Wyliczenie jako parametr.|  
  
### <a name="security"></a>Bezpieczeństwo  
 Prawa dostępu można stosować podczas tworzenia pliku mapowanego na pamięć przy użyciu następujących metod, które przyjmują <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> Wyliczenie jako parametr:  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 Możesz określić prawa dostępu do otwierania istniejącego pliku mapowanego na pamięć przy użyciu metod <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A>, które przyjmują <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> jako parametr.  
  
 Ponadto można uwzględnić obiekt <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity>, który zawiera wstępnie zdefiniowane reguły dostępu.  
  
 Aby zastosować nowe lub zmienione reguły dostępu do pliku mapowanego na pamięć, użyj metody <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A>. Aby pobrać reguły dostępu lub inspekcji z istniejącego pliku, użyj metody <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A>.  
  
## <a name="examples"></a>Przykłady  
  
### <a name="persisted-memory-mapped-files"></a>Utrwalone pliki mapowane w pamięci  
 Metody <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> tworzą plik mapowany w pamięci z istniejącego pliku na dysku.  
  
 Poniższy przykład tworzy widok mapowany w pamięci części bardzo dużego pliku i operuje na jego części.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  
 
[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

 Poniższy przykład powoduje otwarcie tego samego pliku mapowanego na pamięć dla innego procesu.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a>Nieutrwalone pliki mapowane w pamięci  
 Metody <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> i <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> tworzą zamapowane w pamięci plik, który nie jest mapowany na istniejący plik na dysku.  
  
 Poniższy przykład składa się z trzech oddzielnych procesów (aplikacji konsolowych), które zapisują wartości logiczne do pliku mapowanego na pamięć. Występuje następująca sekwencja akcji:  
  
1. `Process A` tworzy plik mapowany w pamięci i zapisuje w nim wartość.  
  
2. `Process B` otwiera plik mapowany w pamięci i zapisuje w nim wartość.  
  
3. `Process C` otwiera plik mapowany w pamięci i zapisuje w nim wartość.  
  
4. `Process A` odczytuje i wyświetla wartości z pliku mapowanego w pamięci.  
  
5. Po zakończeniu `Process A` z plikiem mapowanym w pamięci plik zostanie natychmiast odrzucony przez wyrzucanie elementów bezużytecznych.  
  
 Aby uruchomić ten przykład, wykonaj następujące czynności:  
  
1. Skompiluj aplikacje i otwórz trzy okna wiersza polecenia.  
  
2. W pierwszym oknie wiersza polecenia Uruchom `Process A`.  
  
3. W drugim oknie wiersza polecenia Uruchom `Process B`.  
  
4. Wróć do `Process A` i naciśnij klawisz ENTER.  
  
5. W trzecim oknie wiersza polecenia Uruchom `Process C`.  
  
6. Wróć do `Process A` i naciśnij klawisz ENTER.  
  
 Dane wyjściowe `Process A` są następujące:  
  
```console  
Start Process B and press ENTER to continue.  
Start Process C and press ENTER to continue.  
Process A says: True  
Process B says: False  
Process C says: True  
```  
  
 **Przetwarzaj A**  
  
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
