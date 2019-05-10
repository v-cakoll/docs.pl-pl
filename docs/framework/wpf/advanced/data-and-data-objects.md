---
title: Dane i obiekty danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data transfer [WPF], drag-and-drop
- DataFormats class [WPF]
- DataObject class [WPF]
ms.assetid: 5967d557-1867-420f-a524-ae3af78402da
ms.openlocfilehash: 1e573a3fd175d977d437933d5588c1795851ddc6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64627353"
---
# <a name="data-and-data-objects"></a>Dane i obiekty danych
Dane są przesyłane w ramach operacji przeciągania i upuszczania są przechowywane w obiekcie danych.  Model obiektu danych składa się z co najmniej jedną z następujących par:  
  
- <xref:System.Object> Zawierający rzeczywistych danych.  
  
- Odpowiedni identyfikator format danych.  
  
 Samych danych może zawierać wszystko, co może być reprezentowany jako podstawa <xref:System.Object>.  Odpowiedni format danych jest ciągiem lub <xref:System.Type> zapewniający wskazówkę o tym, co formatowania danych znajduje się w.  Obiekty danych obsługi wiele par format data/data; Dzięki temu obiekt danych jednego dostarczający dane w wielu formatach.  
  
<a name="Data_and_Data_Objects"></a>   
## <a name="data-objects"></a>Obiekty danych  
 Wszystkie obiekty danych musi implementować <xref:System.Windows.IDataObject> interfejs, który oferuje następujący zestaw standardowych metod, które umożliwiają i ułatwienia przesyłania danych.  
  
|Metoda|Podsumowanie|  
|------------|-------------|  
|<xref:System.Windows.IDataObject.GetData%2A>|Pobiera obiekt danych w formacie określone dane.|  
|<xref:System.Windows.IDataObject.GetDataPresent%2A>|Sprawdza, dane są dostępne w, czy można przekonwertować na określony format.|  
|<xref:System.Windows.IDataObject.GetFormats%2A>|Zwraca listę formatów danych w tym obiekcie dane są przechowywane w lub mogą być konwertowane na.|  
|<xref:System.Windows.IDataObject.SetData%2A>|Zapisuje określone dane w ten obiekt danych.|  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dostarcza podstawową implementację <xref:System.Windows.IDataObject> w <xref:System.Windows.DataObject> klasy. Cena akcji <xref:System.Windows.DataObject> klasy jest wystarczająca dla wielu typowych scenariuszy transferu danych.  
  
 Istnieje kilka wstępnie zdefiniowanych formatów, takich jak mapy bitowej, CSV, plik, HTML, RTF, ciąg, tekstu i audio. Informacje na temat formatów danych wstępnie zdefiniowanych dołączonym [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz <xref:System.Windows.DataFormats> temat referencyjny klasy.  
  
 Obiekty danych często obejmują z funkcją automatycznej konwersji danych przechowywanych w jednego formatu do innego formatu podczas wyodrębniania danych. Ten obiekt jest nazywana automatyczna konwersja. Podczas wykonywania zapytań dotyczących formatów danych dostępnych w obiekcie danych, można filtrować formatów danych automatycznie przekonwertować z formatów danych natywnych przez wywołanie metody <xref:System.Windows.DataObject.GetFormats%28System.Boolean%29> lub <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> metody i określając `autoConvert` jako parametr `false`.  Podczas dodawania danych do obiektu danych za pomocą <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29> metody automatycznego Konwersja danych może być zabroniony przez ustawienie `autoConvert` parametr `false`.  
  
<a name="Working_with_Data_Objects"></a>   
## <a name="working-with-data-objects"></a>Praca z obiektami danych  
 W tej sekcji opisano typowe metody do tworzenia i pracy z obiektami danych.  
  
### <a name="creating-new-data-objects"></a>Tworzenie nowych obiektów danych  
 <xref:System.Windows.DataObject> Klasa udostępnia kilka przeciążenia konstruktorów, które ułatwiają wypełnianie nową <xref:System.Windows.DataObject> wystąpienia wraz z przyjacielem format pojedynczego danych.  
  
 Poniższy przykład kodu tworzy nowy obiekt danych i używa jednego z przeciążenia konstruktorów <xref:System.Windows.DataObject.%23ctor%2A>(<xref:System.Windows.DataObject.%23ctor(System.String,System.Object)>) do inicjalizacji obiektu danych przy użyciu ciągu i format określone dane.  W tym przypadku format danych jest określona przez ciąg; <xref:System.Windows.DataFormats> klasa oferuje zestaw wstępnie zdefiniowanych typów ciągów. Konwersja automatycznie przechowywanych danych jest dozwolone domyślnie.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
 Aby uzyskać więcej przykładów kodu, która tworzy obiekt danych, zobacz [utworzyć obiekt danych](how-to-create-a-data-object.md).  
  
### <a name="storing-data-in-multiple-formats"></a>Przechowywanie danych w wielu formatach  
 Obiekt pojedynczego danych jest w stanie do przechowywania danych w wielu formatach.   Strategiczne wykorzystanie wiele formatów danych w obiekcie danych jednego potencjalnie sprawia, że obiekt danych do wykorzystania przez różnych miejsc docelowych, niż tylko format danych jednego mogą być reprezentowane.  Należy pamiętać, że, ogólnie rzecz biorąc, źródła przeciągania musi być niezależny od dotyczących formatów danych, które są do wykorzystania przez potencjalnych miejsc docelowych.  
  
 Poniższy przykład pokazuje, jak używać <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> metodę, aby dodać dane do obiektu danych w wielu formatach.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
### <a name="querying-a-data-object-for-available-formats"></a>Wykonywanie zapytania dotyczącego obiektu danych dla dostępnych formatów  
 Obiekt pojedynczego danych może zawierać dowolną liczbę formatów danych, obiekty danych obejmują funkcje służące do pobierania listy dostępnych formatów danych.  
  
 Poniższy przykład kodu używa <xref:System.Windows.DataObject.GetFormats%2A> przeciążenie, można pobrać tablicę ciągów, określające elementy w obiekcie danych (natywne i przez automatyczna konwersja) wszystkie formaty danych.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
 Aby uzyskać więcej przykładów kodu, który odpytuje obiekt danych dla dostępnych formatów danych, zobacz [listy formatów danych w obiekcie danych](how-to-list-the-data-formats-in-a-data-object.md).  Wykonywanie zapytania dotyczącego obiektu danych na obecność w konkretnym formacie danych, zobacz [ustalić, czy Format danych jest obecny w obiekcie danych](how-to-determine-if-a-data-format-is-present-in-a-data-object.md).  
  
### <a name="retrieving-data-from-a-data-object"></a>Pobieranie danych z obiektu danych  
 Pobieranie danych z obiektu danych, w określonym formacie po prostu polega na wywołaniu jednej z <xref:System.Windows.DataObject.GetData%2A> metody i określanie formatu żądanych danych.  Jedną z <xref:System.Windows.DataObject.GetDataPresent%2A> metody może służyć do sprawdzania obecności w konkretnym formacie danych.  <xref:System.Windows.DataObject.GetData%2A> Zwraca dane w <xref:System.Object>; zależnie od formatu danych ten obiekt może być rzutowany kontenera typu.  
  
 Poniższy przykład kodu używa <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> przeciążenia, aby sprawdzić, czy format określonych danych jest dostępna (natywny lub automatyczna konwersja). Jeśli określony format jest dostępny, przykład pobiera dane przy użyciu <xref:System.Windows.DataObject.GetData%28System.String%29> metody.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
 Aby uzyskać więcej przykładów kodu, który pobiera dane z obiektu danych, zobacz [Pobierz dane w określonym formacie danych](how-to-retrieve-data-in-a-particular-data-format.md).  
  
### <a name="removing-data-from-a-data-object"></a>Usuwanie danych z obiektu danych  
 Danych nie można bezpośrednio usunąć z obiektu danych.  Aby skutecznie usunięcie danych z obiektu danych, wykonaj następujące kroki:  
  
1. Utwórz nowy obiekt danych, która będzie zawierać tylko dane, które mają zostać zachowane.  
  
2. "Kopiuj" żądane dane z stary obiekt danych do nowego obiektu danych.  Aby skopiować dane, użyj jednej z <xref:System.Windows.DataObject.GetData%2A> metody pobierania <xref:System.Object> , zawierający dane pierwotne, a następnie użyj jednej z <xref:System.Windows.DataObject.SetData%2A> metody, aby dodać dane do nowego obiektu danych.  
  
3. Zastąp nowym stary obiekt danych.  
  
> [!NOTE]
>  <xref:System.Windows.DataObject.SetData%2A> Metody tylko dodać dane do obiektu danych; nie zastępują danych, nawet jeśli dane i format danych są dokładnie takie same jak poprzedniego wywołania. Wywoływanie <xref:System.Windows.DataObject.SetData%2A> dwa razy dla tych samych danych i danych spowoduje format w formacie data/data, dwa razy w obiekcie danych.
