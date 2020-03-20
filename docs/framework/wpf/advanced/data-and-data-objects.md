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
ms.openlocfilehash: 532c254f997da183b073ddc9e00b4364ecfcd739
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186338"
---
# <a name="data-and-data-objects"></a>Dane i obiekty danych
Dane przesyłane w ramach operacji przeciągania i upuszczania są przechowywane w obiekcie danych.  Koncepcyjnie obiekt danych składa się z jednej lub więcej z następujących par:  
  
- An, <xref:System.Object> który zawiera rzeczywiste dane.  
  
- Odpowiedni identyfikator formatu danych.  
  
 Same dane mogą składać się z wszystkiego, <xref:System.Object>co może być reprezentowane jako podstawa.  Odpowiedni format danych jest <xref:System.Type> ciągiem lub który zawiera wskazówkę o tym, w jakim formacie znajdują się dane.  Obiekty danych obsługują obsługę wielu par formatu danych/danych; umożliwia to pojedynczy obiekt danych, aby zapewnić dane w wielu formatach.  
  
<a name="Data_and_Data_Objects"></a>
## <a name="data-objects"></a>Obiekty danych  
 Wszystkie obiekty danych <xref:System.Windows.IDataObject> muszą implementować interfejs, który zawiera następujący standardowy zestaw metod, które umożliwiają i ułatwiają przesyłanie danych.  
  
|Metoda|Podsumowanie|  
|------------|-------------|  
|<xref:System.Windows.IDataObject.GetData%2A>|Pobiera obiekt danych w określonym formacie danych.|  
|<xref:System.Windows.IDataObject.GetDataPresent%2A>|Sprawdza, czy dane są dostępne w określonym formacie lub można je przekonwertować.|  
|<xref:System.Windows.IDataObject.GetFormats%2A>|Zwraca listę formatów, w których dane w tym obiekcie danych są przechowywane lub można je przekonwertować.|  
|<xref:System.Windows.IDataObject.SetData%2A>|Przechowuje określone dane w tym obiekcie danych.|  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zapewnia podstawową <xref:System.Windows.IDataObject> implementację <xref:System.Windows.DataObject> w klasie. Klasa <xref:System.Windows.DataObject> zapasów jest wystarczająca dla wielu typowych scenariuszy transferu danych.  
  
 Istnieje kilka wstępnie zdefiniowanych formatów, takich jak bitmapa, CSV, plik, HTML, RTF, ciąg, tekst i dźwięk. Aby uzyskać informacje na temat wstępnie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zdefiniowanych <xref:System.Windows.DataFormats> formatów danych dostarczonych z , zobacz temat odwołania do klasy.  
  
 Obiekty danych często obejmują możliwość automatycznego konwertowania danych przechowywanych w jednym formacie na inny format podczas wyodrębniania danych; ta funkcja jest określana jako automatyczna konwersja. Podczas wykonywania zapytań o formaty danych dostępne w obiekcie danych, automatyczne konwertowanie formatów <xref:System.Windows.DataObject.GetFormats%28System.Boolean%29> <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> danych można filtrować z natywnych formatów danych, wywołując lub metodę i określając `autoConvert` parametr jako `false`.  Podczas dodawania danych do <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29> obiektu danych za pomocą metody, automatyczna `autoConvert` konwersja `false`danych może być zabroniona przez ustawienie parametru na .  
  
<a name="Working_with_Data_Objects"></a>
## <a name="working-with-data-objects"></a>Praca z obiektami danych  
 W tej sekcji opisano typowe techniki tworzenia i pracy z obiektami danych.  
  
### <a name="creating-new-data-objects"></a>Tworzenie nowych obiektów danych  
 Klasa <xref:System.Windows.DataObject> zawiera kilka przeciążonych konstruktorów, <xref:System.Windows.DataObject> które ułatwiają wypełnianie nowego wystąpienia za pomocą jednej pary formatu danych/danych.  
  
 Poniższy przykładowy kod tworzy nowy obiekt danych i używa <xref:System.Windows.DataObject.%23ctor%2A>jednego<xref:System.Windows.DataObject.%23ctor(System.String,System.Object)>z przeciążonych konstruktorów ( ) do zainicjowania obiektu danych za pomocą ciągu i określonego formatu danych.  W takim przypadku format danych jest określony przez ciąg; <xref:System.Windows.DataFormats> klasa zawiera zestaw wstępnie zdefiniowanych ciągów typu. Domyślnie dozwolona jest automatyczna konwersja przechowywanych danych.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
 Aby uzyskać więcej przykładów kodu, który tworzy obiekt danych, zobacz [Tworzenie obiektu danych](how-to-create-a-data-object.md).  
  
### <a name="storing-data-in-multiple-formats"></a>Przechowywanie danych w wielu formatach  
 Pojedynczy obiekt danych może przechowywać dane w wielu formatach.   Strategiczne użycie wielu formatów danych w obrębie jednego obiektu danych potencjalnie sprawia, że obiekt danych jest zużywalny przez szerszą różnorodność obiektów docelowych upuszczania, niż gdyby można było reprezentować tylko jeden format danych.  Należy zauważyć, że ogólnie źródło przeciągania musi być niezależny od formatów danych, które są używane przez potencjalne cele upuszczania.  
  
 W poniższym przykładzie <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> pokazano, jak użyć metody do dodawania danych do obiektu danych w wielu formatach.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
### <a name="querying-a-data-object-for-available-formats"></a>Wykonywanie zapytań o obiekt danych w dostępnych formatach  
 Ponieważ pojedynczy obiekt danych może zawierać dowolną liczbę formatów danych, obiekty danych zawierają funkcje pobierania listy dostępnych formatów danych.  
  
 Poniższy przykładowy kod <xref:System.Windows.DataObject.GetFormats%2A> używa przeciążenia, aby uzyskać tablicę ciągów oznaczających wszystkie formaty danych dostępne w obiekcie danych (zarówno natywne, jak i automatycznie konwertowane).  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
 Aby uzyskać więcej przykładów kodu, który wysyła kwerendy do obiektu danych dla dostępnych formatów danych, zobacz [Lista formatów danych w obiekcie danych](how-to-list-the-data-formats-in-a-data-object.md).  Aby zapoznać się z przykładami wykonywania zapytań o obiekt danych pod kątem obecności określonego formatu danych, zobacz [Określanie, czy format danych jest obecny w obiekcie danych](how-to-determine-if-a-data-format-is-present-in-a-data-object.md).  
  
### <a name="retrieving-data-from-a-data-object"></a>Pobieranie danych z obiektu danych  
 Pobieranie danych z obiektu danych w określonym formacie polega <xref:System.Windows.DataObject.GetData%2A> po prostu na wywoływaniu jednej z metod i określaniu żądanego formatu danych.  Jedną z <xref:System.Windows.DataObject.GetDataPresent%2A> metod można użyć do sprawdzenia obecności określonego formatu danych.  <xref:System.Windows.DataObject.GetData%2A>zwraca dane w <xref:System.Object>; w zależności od formatu danych, ten obiekt może być rzutowy do kontenera specyficznego dla typu.  
  
 Poniższy przykładowy kod <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> używa przeciążenia, aby sprawdzić, czy określony format danych jest dostępny (natywny lub przez automatyczną konwersję). Jeśli określony format jest dostępny, przykład pobiera dane <xref:System.Windows.DataObject.GetData%28System.String%29> przy użyciu metody.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
 Aby uzyskać więcej przykładów kodu pobieranego danych z obiektu danych, zobacz [Pobieranie danych w określonym formacie danych](how-to-retrieve-data-in-a-particular-data-format.md).  
  
### <a name="removing-data-from-a-data-object"></a>Usuwanie danych z obiektu danych  
 Dane nie mogą być bezpośrednio usunięte z obiektu danych.  Aby skutecznie usunąć dane z obiektu danych, wykonaj następujące kroki:  
  
1. Utwórz nowy obiekt danych, który będzie zawierał tylko te dane, które chcesz zachować.  
  
2. "Skopiuj" żądane dane ze starego obiektu danych do nowego obiektu danych.  Aby skopiować dane, użyj <xref:System.Windows.DataObject.GetData%2A> jednej z <xref:System.Object> metod, aby pobrać, który zawiera <xref:System.Windows.DataObject.SetData%2A> nieprzetworzone dane, a następnie użyj jednej z metod, aby dodać dane do nowego obiektu danych.  
  
3. Zastąp stary obiekt danych nowym.  
  
> [!NOTE]
> Metody <xref:System.Windows.DataObject.SetData%2A> tylko dodać dane do obiektu danych; nie zastępują danych, nawet jeśli format danych i danych są dokładnie takie same jak poprzednie wywołanie. Wywołanie <xref:System.Windows.DataObject.SetData%2A> dwukrotnie dla tego samego formatu danych i danych spowoduje, że format danych/danych będzie obecny dwukrotnie w obiekcie danych.
