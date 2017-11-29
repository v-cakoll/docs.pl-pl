---
title: "Pliki mapowane w pamięci"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- memory-mapped files
- inter-process communiation
ms.assetid: a483d1b5-64aa-45b6-86ef-11b859f7f02e
caps.latest.revision: "24"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2602d431aada7b3e0ee226eed319903492022ae9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="memory-mapped-files"></a>Pliki mapowane w pamięci
Zawartość pliku w pamięci wirtualnej zawiera plik mapowanych na pamięć. To mapowanie między pliku i pamięci miejsca umożliwia aplikacji, w tym wiele procesów zmodyfikować plik przy odczytywanie i zapisywanie bezpośrednio do pamięci. Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], można użyć kodu zarządzanego do dostępu do plików mapowanych na pamięć w taki sam sposób, że funkcje natywne Windows dostępu pliki mapowane w pamięci, zgodnie z opisem w [Managing Memory-Mapped plików w systemie Win32](http://go.microsoft.com/fwlink/?linkid=180801).  
  
 Istnieją dwa typy plików mapowanych na pamięć:  
  
-   Trwałe pliki mapowane w pamięci  
  
     Trwałe pliki są pliki mapowane w pamięci, które są skojarzone z plikiem źródłowym na dysku. Gdy ostatni proces zakończył pracę z plikiem, dane są zapisywane do pliku źródłowego na dysku. Te pliki mapowane w pamięci są odpowiednie do pracy z plikami źródłowymi bardzo duże.  
  
-   Non utrwalony pliki mapowane w pamięci  
  
     Non utrwalony pliki są pliki mapowane w pamięci, które nie są skojarzone z plikiem na dysku. Ostatni proces zakończył pracę z plikiem, dane zostaną utracone, a plik jest odzyskana przez wyrzucanie elementów bezużytecznych. Pliki te są odpowiednie do tworzenia pamięci współużytkowanej komunikacji międzyprocesowej (IPC).  
  
## <a name="processes-views-and-managing-memory"></a>Procesy, widoków i zarządzanie pamięci  
 Pliki mapowane w pamięci może być współużytkowana przez wiele procesów. Procesy można mapować do tego samego pliku mapowanych na pamięć przy użyciu nazwą pospolitą, który jest przypisywany przez proces tworzenia pliku.  
  
 Aby pracować z plikiem mapowanych na pamięć, należy utworzyć widok cały plik mapowanych na pamięć lub jego część. Można również utworzyć wiele widoków na tę samą część plików mapowanych na pamięć, tworząc równoczesnych pamięci. Dla dwóch widoków pozostaje jednoczesnych muszą być utworzone na podstawie tego samego pliku mapowanych na pamięć.  
  
 Wiele widoków może być również konieczne, jeśli plik jest większy niż rozmiar przestrzeni pamięci logicznej aplikacji dostępnej pamięci mapowania (2 GB na komputerze 32-bitowym).  
  
 Istnieją dwa typy widoków: strumienia widok dostępu i dostępie. Używanie widoków dostęp do strumienia sekwencyjnego dostępu do pliku; jest to zalecane dla-utrwalony plików i IPC. Widoki dostęp losowy są preferowane w przypadku pracy z plikami utrwalonych.  
  
 Pliki mapowane w pamięci są dostępne za pośrednictwem Menedżera pamięci systemu operacyjnego, więc plik automatycznie jest podzielona na partycje na kilka stron i dostępne w razie potrzeby. Nie masz do obsługi zarządzania pamięcią, samodzielnie.  
  
 Na poniższej ilustracji przedstawiono sposób wiele procesów może mieć wiele i nakładanie się widoków do tego samego pliku mapowane w pamięci w tym samym czasie.  
  
 ![Przedstawia widok pamięci &#45; zamapowanego pliku. ] (../../../docs/standard/io/media/memmappersisted.png "MemMapPersisted")  
Wiele i nakładany widoków do pliku mapowanych na pamięć  
  
## <a name="programming-with-memory-mapped-files"></a>Programowanie za pomocą plików mapowanych na pamięć  
 W poniższej tabeli przedstawiono przedstawiono wskazówki dotyczące korzystania z plików mapowanych na pamięć obiektów i ich elementy członkowskie.  
  
|Zadanie|Metody lub właściwości do użycia|  
|----------|----------------------------------|  
|Aby uzyskać <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> obiekt, który reprezentuje utrwalonego pliku mapowanych na pamięć z pliku na dysku.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>Metoda.|  
|Aby uzyskać <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> obiekt, który reprezentuje plik mapowanych na pamięć nietrwałe (nie są skojarzone z plikiem na dysku).|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>Metoda.<br /><br /> - lub -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>Metoda.|  
|Aby uzyskać <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> obiektu istniejący plik mapowanych na pamięć (utrwalonego lub -utrwalony).|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType>Metoda.|  
|Aby uzyskać <xref:System.IO.UnmanagedMemoryStream> obiektu dla widoku sekwencyjnie dostępu do plików mapowanych na pamięć.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType>Metoda.|  
|Aby uzyskać <xref:System.IO.UnmanagedMemoryAccessor> obiekt widoku dostępie swobodnym mapować pamięci pole.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType>Metoda.|  
|Aby uzyskać <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> obiekt ma być używany z kodem niezarządzanym.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType>Właściwość.<br /><br /> - lub -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>Właściwość.<br /><br /> - lub -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>Właściwość.|  
|Opóźnienia przydzielania pamięci do widok jest tworzony (tylko-utrwalony pliki).<br /><br /> (Aby określić bieżącego rozmiaru strony systemowej, użyj <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> właściwości.)|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A>metody z <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> wartości.<br /><br /> - lub -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A>metody, które mają <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> wyliczenie jako parametr.|  
  
### <a name="security"></a>Zabezpieczenia  
 Prawa dostępu można zastosować podczas tworzenia pliku mapowanych na pamięć przy użyciu następujących metod, które przyjmują <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> wyliczenie jako parametr:  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 Można określić prawa dostępu do otwierania istniejącego pliku mapowanych na pamięć przy użyciu <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> metod, które przyjmują <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> jako parametr.  
  
 Ponadto można uwzględnić <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> obiekt, który zawiera reguły dostępu wstępnie zdefiniowane.  
  
 Aby zastosować reguły dostępu do nowych lub zmienionych plików mapowanych na pamięć, użyj <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> metody. Aby pobrać dostępu lub inspekcji reguły z istniejącego pliku, użyj <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> metody.  
  
## <a name="examples"></a>Przykłady  
  
### <a name="persisted-memory-mapped-files"></a>Trwałe pliki mapowane w pamięci  
 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> Metody tworzenia plików mapowanych na pamięć z istniejącego pliku na dysku.  
  
 Poniższy przykład tworzy widok część bardzo dużych plików mapowanych na pamięć i manipuluje część.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  
  
 Poniższy przykład powoduje otwarcie tego samego pliku mapowanych na pamięć na inny proces.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a>-Utrwalony pliki mapowane w pamięci  
 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> i <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> metody tworzenia mapowanych na pamięć pliku, który nie jest zamapowany do istniejącego pliku na dysku.  
  
 Poniższy przykład składa się z trzech osobnych procesach (aplikacji konsoli), wartościami logicznymi zapisu w pliku mapowanych na pamięć. Występuje następująca sekwencja akcji:  
  
1.  `Process A`Tworzy plik mapowanych na pamięć i zapisuje wartość.  
  
2.  `Process B`Otwiera plik mapowanych na pamięć i zapisuje wartość.  
  
3.  `Process C`Otwiera plik mapowanych na pamięć i zapisuje wartość.  
  
4.  `Process A`odczytuje i wyświetla wartości z pliku mapowanych na pamięć.  
  
5.  Po `Process A` zostało zakończone z plików mapowanych na pamięć pliku natychmiast odzyskana przez wyrzucanie elementów bezużytecznych.  
  
 Aby uruchomić ten przykład, wykonaj następujące czynności:  
  
1.  Kompilowanie aplikacji i trzy okna wiersza polecenia.  
  
2.  W pierwszym oknie wiersza polecenia, uruchom `Process A`.  
  
3.  W oknie wiersza polecenia drugiej Uruchom `Process B`.  
  
4.  Wróć do `Process A` i naciśnij klawisz ENTER.  
  
5.  W trzecim okno wiersza polecenia, uruchom `Process C`.  
  
6.  Wróć do `Process A` i naciśnij klawisz ENTER.  
  
 Dane wyjściowe `Process A` wygląda następująco:  
  
```  
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
 [Plik i strumienia I-O](../../../docs/standard/io/index.md)
