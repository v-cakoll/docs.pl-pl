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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f7bda02e1862740e6a6328835367a6a5e9929033
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026080"
---
# <a name="memory-mapped-files"></a>Pliki mapowane w pamięci
Plik mapowany w pamięci zawiera zawartość pliku w pamięci wirtualnej. To mapowanie między pliku i pamięci miejsca umożliwia aplikacji, w tym wiele procesów można modyfikować plik przez odczyt i zapis bezpośrednio do pamięci. Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], można użyć kodu zarządzanego dostępu do zamapowanych w pamięci plików w taki sam sposób, że funkcji natywnych Windows dostęp do plików zamapowanych w pamięci, zgodnie z opisem w [pliki Managing Memory-Mapped](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10)).  
  
 Istnieją dwa typy plików zamapowanych w pamięci:  
  
- Trwałe pliki mapowane w pamięci  
  
     Trwałe pliki są pliki mapowane w pamięci, które są skojarzone z plikiem źródłowym, na dysku. Podczas ostatniego proces zakończył pracę z plikiem, dane są zapisywane do pliku źródłowego na dysku. Te pliki mapowane w pamięci są odpowiednie do pracy z plikami źródłowymi bardzo duże.  
  
- Trwały inne niż pliki mapowane w pamięci  
  
     Trwały inne niż pliki są pliki mapowane w pamięci, które nie są skojarzone z plikiem na dysku. Podczas ostatniego proces zakończył pracę z plikiem, dane zostaną utracone, a plik jest odzyskiwane przez wyrzucanie elementów bezużytecznych. Te pliki są odpowiednie do tworzenia współużytkowaną pamięć służącą do komunikacji międzyprocesowej (IPC).  
  
## <a name="processes-views-and-managing-memory"></a>Procesy, widoków i zarządzanie pamięci  
 Pliki mapowane w pamięci mogą być współużytkowane przez wiele procesów. Procesy można mapować do tego samego pliku mapowanych na pamięć przy użyciu nazwą pospolitą, który jest przypisywany przez proces, która utworzyła plik.  
  
 Aby pracować z plikiem mapowane w pamięci, należy utworzyć widok całego pliku mapowanych na pamięć lub jej część. Można również utworzyć wiele widoków, aby tę samą część plików zamapowanych w pamięci, tworząc w ten sposób pamięcią współbieżną. Dla dwóch widoków pozostaje współbieżnych muszą oni można tworzyć na podstawie tego samego pliku mapowanych na pamięć.  
  
 Wiele widoków, może być również konieczne, jeśli plik jest większy niż rozmiar aplikacji logicznej pamięci miejsce dostępne na potrzeby mapowania (2 GB na komputerze 32-bitowy) pamięci.  
  
 Istnieją dwa typy widoków: przesyłanie strumieniowe dostępu do widoku oraz widoku swobodnego dostępu. Strumień dostępu do widoków na użytek dostępu sekwencyjnego do pliku; jest to zalecane w przypadku plików nietrwałe i IPC. Widoki swobodnego dostępu są preferowane w przypadku pracy z plikami utrwalonych.  
  
 Pliki mapowane w pamięci są dostępne za pośrednictwem Menedżera pamięci systemu operacyjnego, plik automatycznie zostanie poddana partycjonowaniu na liczbę stron i dostępne, zgodnie z potrzebami. Nie masz do obsługi zarządzania pamięcią, samodzielnie.  
  
 Na poniższej ilustracji przedstawiono sposób wielu procesów może mieć wiele i nakładających się widoki do tego samego pliku mapowane w pamięci, w tym samym czasie.

 Poniższa ilustracja przedstawia wiele i nakładających się widoków z plikiem mapowane w pamięci:  
  
 ![Zrzut ekranu pokazujący widoki pamięci&#45;mapowane pliku.](./media/memory-mapped-files/memory-map-persist-file.png)  
  
## <a name="programming-with-memory-mapped-files"></a>Programowanie za pomocą pliki mapowane w pamięci  
 W poniższej tabeli przedstawiono wskazówki dotyczące korzystania z obiektów plików zamapowanych w pamięci oraz ich elementów członkowskich.  
  
|Zadanie|Metody lub właściwości do użycia|  
|----------|----------------------------------|  
|Aby uzyskać <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> obiekt, który reprezentuje utrwalonego pliku mapowane w pamięci z pliku na dysku.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> Metoda.|  
|Aby uzyskać <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> obiekt, który reprezentuje plik mapowanych na pamięć nietrwałe (nie skojarzonych z plikiem na dysku).|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> Metoda.<br /><br /> - lub -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> Metoda.|  
|Aby uzyskać <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> obiekt istniejący plik mapowane w pamięci (utrwalona lub nieutrwaloną).|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> Metoda.|  
|Aby uzyskać <xref:System.IO.UnmanagedMemoryStream> obiektu w celu wyświetlenia sekwencyjnie używanych do plików mapowanych na pamięć.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> Metoda.|  
|Aby uzyskać <xref:System.IO.UnmanagedMemoryAccessor> obiektu w celu wyświetlenia swobodnego dostępu do zamapowanych w pamięci plik.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> Metoda.|  
|Aby uzyskać <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> obiekt ma być używany z kodem niezarządzanym.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> Właściwość.<br /><br /> - lub -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> Właściwość.<br /><br /> - lub -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> Właściwość.|  
|Opóźnienia alokacji pamięci, aż widok jest tworzony (tylko nieutrwaloną pliki).<br /><br /> (Aby określić bieżący rozmiar strony systemowej, należy użyć <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> właściwości.)|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> Metoda o <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> wartość.<br /><br /> - lub -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> metody, które mają <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> wyliczenia jako parametr.|  
  
### <a name="security"></a>Zabezpieczenia  
 Prawa dostępu można zastosować podczas tworzenia pliku mapowanych na pamięć przy użyciu następujących metod, które przyjmują <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> wyliczenia jako parametr:  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 Można określić uprawnienia do otwierania istniejącego pliku mapowanych na pamięć przy użyciu <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> metod, które przyjmują <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> jako parametr.  
  
 Ponadto, możesz dołączyć <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> obiekt, który zawiera reguły dostępu do wstępnie zdefiniowane.  
  
 Aby zastosować reguły dostępu do nowych lub zmienionych plików zamapowanych w pamięci, należy użyć <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> metody. Aby pobrać dostępu lub inspekcji reguły z istniejącego pliku, użyj <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> metody.  
  
## <a name="examples"></a>Przykłady  
  
### <a name="persisted-memory-mapped-files"></a>Trwałe pliki mapowane w pamięci  
 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> Metod tworzenia pliku mapowane w pamięci z istniejącego pliku na dysku.  
  
 Poniższy przykład tworzy widok część bardzo dużych plików zamapowanych w pamięci i manipuluje jego części.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  
  
 W poniższym przykładzie otwierany tego samego pliku mapowanych na pamięć na inny proces.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a>Nietrwałe pliki mapowane w pamięci  
 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> i <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> metody tworzenia plików mapowanych na pamięć, który nie jest zamapowany do istniejącego pliku na dysku.  
  
 Poniższy przykład składa się z trzech osobnych procesach (aplikacje konsoli), wartościami logicznymi zapisu w pliku mapowanych na pamięć. Występuje następującą sekwencję czynności:  
  
1. `Process A` Tworzy plik mapowany w pamięci i zapisuje wartość.  
  
2. `Process B` Otwiera plik mapowany w pamięci i zapisuje wartość.  
  
3. `Process C` Otwiera plik mapowany w pamięci i zapisuje wartość.  
  
4. `Process A` odczytuje i wyświetla wartości z pliku mapowanych na pamięć.  
  
5. Po `Process A` zostało zakończone z plikiem mapowane w pamięci, plik jest natychmiast odzyskiwane przez wyrzucanie elementów bezużytecznych.  
  
 Aby uruchomić ten przykład, wykonaj następujące czynności:  
  
1. Kompiluj aplikacje, a następnie otwórz trzy okna wiersza polecenia.  
  
2. W pierwszym oknie wiersza polecenia, uruchom `Process A`.  
  
3. W drugim oknie wiersza polecenia, uruchom `Process B`.  
  
4. Wróć do `Process A` i naciśnij klawisz ENTER.  
  
5. W trzecim okno wiersza polecenia, uruchom `Process C`.  
  
6. Wróć do `Process A` i naciśnij klawisz ENTER.  
  
 Dane wyjściowe `Process A` jest następująca:  
  
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
  
## <a name="see-also"></a>Zobacz także

- [We/Wy plików i strumieni](../../../docs/standard/io/index.md)
