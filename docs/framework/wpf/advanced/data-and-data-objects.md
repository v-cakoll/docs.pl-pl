---
title: Dane i obiekty danych
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data transfer [WPF], drag-and-drop
- DataFormats class [WPF]
- DataObject class [WPF]
ms.assetid: 5967d557-1867-420f-a524-ae3af78402da
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fc5d5f8c2090f6abaa1157db2a92d2e689d7f216
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="data-and-data-objects"></a>Dane i obiekty danych
Dane są przesyłane w ramach operacji przeciągania i upuszczania są przechowywane w obiekcie danych.  Koncepcyjnie obiekt danych składa się z co najmniej jeden z następujących par:  
  
-   <xref:System.Object> Zawierający dane.  
  
-   Odpowiedni identyfikator formatu danych.  
  
 Samych danych może zawierać wszystko, co może być reprezentowany jako podstawa <xref:System.Object>.  Odpowiedni format danych jest ciągiem lub <xref:System.Type> zapewnia wskazówki dotyczące formatowania co danych znajduje się w.  Obiekty danych obsługi wielu pary format danych i danych; Dzięki temu obiekt danych jednego dostarczający dane w wielu formatach.  
  
<a name="Data_and_Data_Objects"></a>   
## <a name="data-objects"></a>Obiekty danych  
 Wszystkie obiekty danych musi implementować <xref:System.Windows.IDataObject> interfejs, który oferuje następujący zestaw standardowych metod umożliwiające i ułatwienia przenoszenia danych.  
  
|Metoda|Podsumowanie|  
|------------|-------------|  
|<xref:System.Windows.IDataObject.GetData%2A>|Pobiera obiekt danych w formacie określone dane.|  
|<xref:System.Windows.IDataObject.GetDataPresent%2A>|Sprawdza, czy dane są dostępne w lub można przekonwertować na określony format.|  
|<xref:System.Windows.IDataObject.GetFormats%2A>|Zwraca listę formatów, które dane w tym obiekcie danych są przechowywane w lub może zostać przekonwertowany na.|  
|<xref:System.Windows.IDataObject.SetData%2A>|Zapisuje określone dane w tym obiekcie danych.|  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]udostępnia podstawową implementację elementu <xref:System.Windows.IDataObject> w <xref:System.Windows.DataObject> klasy. Zasoby <xref:System.Windows.DataObject> klasy jest wystarczająca dla wielu typowych scenariuszy transferu danych.  
  
 Istnieje kilka wstępnie zdefiniowanych formatów, takich jak mapy bitowej, CSV, pliku, HTML, RTF, string, tekst i audio. Informacje na temat wstępnie zdefiniowanych danych formatów wyposażone [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz <xref:System.Windows.DataFormats> temat referencyjny klasy.  
  
 Obiekty danych zwykle obejmują z funkcją automatycznej konwersji danych przechowywanych w jednego formatu na inny format podczas wyodrębniania danych; tej funkcji jest określana jako automatyczną konwersję. Podczas wykonywania zapytania formatów danych dostępnych w obiekcie danych, można filtrować formaty danych możliwe do przekonwertowania automatycznie z formatów danych natywnych przez wywołanie metody <xref:System.Windows.DataObject.GetFormats%28System.Boolean%29> lub <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> — metoda i określając `autoConvert` parametr jako `false`.  Podczas dodawania danych do obiektu o danych <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29> metody autokonwersję danych można zabronione przez ustawienie `autoConvert` parametr `false`.  
  
<a name="Working_with_Data_Objects"></a>   
## <a name="working-with-data-objects"></a>Praca z obiektami danych  
 W tej sekcji opisano typowe techniki tworzenia i Praca z obiektami danych.  
  
### <a name="creating-new-data-objects"></a>Tworzenie nowych obiektów danych  
 <xref:System.Windows.DataObject> Klasa udostępnia kilka konstruktorów przeciążone ułatwienia wypełniania nowy <xref:System.Windows.DataObject> wystąpienia przy użyciu pary format jednego danych.  
  
 Poniższy przykładowy kod tworzy nowy obiekt danych i korzysta z jednego z konstruktorów przeciążone <xref:System.Windows.DataObject.%23ctor%2A>(<xref:System.Windows.DataObject.%23ctor(System.String,System.Object)>) do inicjalizacji obiektu dane z ciągu i format określonych danych.  W takim przypadku format danych jest określona przez ciąg. <xref:System.Windows.DataFormats> klasa udostępnia zestaw ciągów wstępnie zdefiniowanego typu. Domyślnie dozwolone jest autokonwersję przechowywanych danych.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
 Aby uzyskać więcej przykładów kodu, który tworzy obiekt danych, zobacz [utworzyć obiektu danych](../../../../docs/framework/wpf/advanced/how-to-create-a-data-object.md).  
  
### <a name="storing-data-in-multiple-formats"></a>Przechowywanie danych w wielu formatach  
 Obiekt pojedynczego danych jest w stanie do przechowywania danych w wielu formatach.   Strategiczne użycie wielu formatów danych w obiekcie danych jednego potencjalnie sprawia, że obiekt danych dostępne różnych miejsc docelowych niż jeśli tylko format danych jednego może być reprezentowany.  Należy pamiętać, że, ogólnie rzecz biorąc, źródła przeciągania musi być niezależny formaty danych, które są dostępne potencjalnych miejsc docelowych.  
  
 Poniższy przykład przedstawia użycie <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> metody, aby dodać dane do obiektu danych w wielu formatach.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
### <a name="querying-a-data-object-for-available-formats"></a>Wyszukiwanie obiektu danych dostępnych formatów  
 Obiekt pojedynczego danych może zawierać dowolną liczbę formatów danych, obiekty danych obejmują urządzenia do pobierania listy dostępnych formatów danych.  
  
 Poniższy przykład kodu wykorzystuje <xref:System.Windows.DataObject.GetFormats%2A> przeciążenia uzyskać tablicę ciągów określające wszystkie formaty danych dostępne w obiekcie danych (natywny i przez automatyczną konwersję).  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
 Więcej przykładów kodu, który odpytuje obiekt danych dostępnych danych formatów, zobacz [listy formatów danych w obiekcie danych](../../../../docs/framework/wpf/advanced/how-to-list-the-data-formats-in-a-data-object.md).  Przykłady zapytań obiekt danych na obecność format danych, zobacz [ustalić, czy Format danych jest obecnie w obiekcie danych](../../../../docs/framework/wpf/advanced/how-to-determine-if-a-data-format-is-present-in-a-data-object.md).  
  
### <a name="retrieving-data-from-a-data-object"></a>Pobieranie danych z obiektu danych  
 Pobieranie danych z obiektu danych w określonym formacie po prostu obejmuje wywołaniem <xref:System.Windows.DataObject.GetData%2A> metody i określanie formatu żądanych danych.  Jeden z <xref:System.Windows.DataObject.GetDataPresent%2A> metod można sprawdzić obecność formatu danych.  <xref:System.Windows.DataObject.GetData%2A>Zwraca dane w <xref:System.Object>; zależnie od formatu danych tego obiektu mogą być rzutowane na kontenera określonego typu.  
  
 Poniższy przykład kodu wykorzystuje <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> przeciążenia, aby sprawdzić, czy format określonych danych jest dostępna (natywny lub automatyczną konwersję). Jeśli określony format jest dostępny, przykładzie pobiera dane przy użyciu <xref:System.Windows.DataObject.GetData%28System.String%29> metody.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
 Aby uzyskać więcej przykładów kodu, który pobiera dane z obiektu danych, zobacz [pobieranie danych w określonym formacie danych](../../../../docs/framework/wpf/advanced/how-to-retrieve-data-in-a-particular-data-format.md).  
  
### <a name="removing-data-from-a-data-object"></a>Usuwanie danych z obiektu danych  
 Danych nie można bezpośrednio usunąć z obiektu danych.  Aby skutecznie usunięcie danych z obiektu danych, wykonaj następujące kroki:  
  
1.  Utwórz nowy obiekt danych, który będzie zawierać tylko dane, które chcesz zachować.  
  
2.  "Kopiuj" żądanych danych z stary obiekt danych do nowego obiektu danych.  Aby skopiować dane, użyj jednej z <xref:System.Windows.DataObject.GetData%2A> metody do pobierania <xref:System.Object> zawiera dane pierwotne, a następnie użyj jednej z <xref:System.Windows.DataObject.SetData%2A> metody dodawania danych do nowego obiektu danych.  
  
3.  Zamień stary obiekt danych na nowym.  
  
> [!NOTE]
>  <xref:System.Windows.DataObject.SetData%2A> Metody tylko dodać dane do obiektu danych; nie zastępują danych, nawet jeśli dane i format danych są dokładnie takie same jak poprzednie wywołanie. Wywoływanie <xref:System.Windows.DataObject.SetData%2A> dwukrotnie dla tych samych danych i dane formatu spowoduje w formacie danych/obecności dwa razy w obiekcie danych.
