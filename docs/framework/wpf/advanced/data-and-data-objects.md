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
ms.openlocfilehash: 4b948a64a14df7ea79b54b810f734056d57ef406
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964864"
---
# <a name="data-and-data-objects"></a>Dane i obiekty danych
Dane przesyłane w ramach operacji przeciągania i upuszczania są przechowywane w obiekcie danych.  Koncepcyjnie obiekt danych składa się z co najmniej jednej z następujących par:  
  
- <xref:System.Object> Zawierający rzeczywiste dane.  
  
- Odpowiedni identyfikator formatu danych.  
  
 Dane mogą zawierać wszystko, co może być reprezentowane jako baza <xref:System.Object>.  Odpowiedni format danych jest ciągiem lub <xref:System.Type> zawierającym wskazówkę dotyczącą formatu, w którym znajdują się dane.  Obiekty danych obsługują hostowanie wielu par danych/formatów danych; Dzięki temu pojedynczy obiekt danych może dostarczyć dane w wielu formatach.  
  
<a name="Data_and_Data_Objects"></a>   
## <a name="data-objects"></a>Obiekty danych  
 Wszystkie obiekty danych muszą implementować <xref:System.Windows.IDataObject> interfejs, który zapewnia następujący standardowy zestaw metod, które umożliwiają i ułatwiają transfer danych.  
  
|Metoda|Podsumowanie|  
|------------|-------------|  
|<xref:System.Windows.IDataObject.GetData%2A>|Pobiera obiekt danych w określonym formacie danych.|  
|<xref:System.Windows.IDataObject.GetDataPresent%2A>|Sprawdza, czy dane są dostępne w programie, czy można je przekonwertować na format w określonym formacie.|  
|<xref:System.Windows.IDataObject.GetFormats%2A>|Zwraca listę formatów, w których przechowywane są dane w tym obiekcie danych lub które można przekonwertować na.|  
|<xref:System.Windows.IDataObject.SetData%2A>|Zapisuje określone dane w tym obiekcie danych.|  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]udostępnia podstawową implementację <xref:System.Windows.IDataObject> <xref:System.Windows.DataObject> w klasie. Klasa Stock <xref:System.Windows.DataObject> jest wystarczająca dla wielu typowych scenariuszy transferu danych.  
  
 Istnieje kilka wstępnie zdefiniowanych formatów, takich jak bitmapy, CSV, plik, HTML, RTF, String, text i audio. Informacje o wstępnie zdefiniowanych formatach danych dostępnych w programie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]można znaleźć w <xref:System.Windows.DataFormats> temacie Informacje o klasie.  
  
 Obiekty danych często obejmują funkcję służącą do automatycznego konwertowania danych przechowywanych w jednym formacie na inny format podczas wyodrębniania danych; Ta funkcja jest nazywana autokonwertowaniem. Podczas wykonywania zapytania o formaty danych dostępne w obiekcie danych, formaty danych z możliwością skalowania mogą być filtrowane z natywnych formatów danych przez wywołanie <xref:System.Windows.DataObject.GetFormats%28System.Boolean%29> metody <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> lub i określenie `autoConvert` parametru jako `false`.  Podczas dodawania danych do obiektu danych przy użyciu <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29> metody, funkcja autokonwersji danych może być zabroniona przez `autoConvert` ustawienie parametru na `false`.  
  
<a name="Working_with_Data_Objects"></a>   
## <a name="working-with-data-objects"></a>Praca z obiektami danych  
 W tej sekcji opisano typowe techniki tworzenia obiektów danych i pracy z tymi obiektami.  
  
### <a name="creating-new-data-objects"></a>Tworzenie nowych obiektów danych  
 Klasa zawiera kilka przeciążonych konstruktorów, które ułatwiają <xref:System.Windows.DataObject> zapełnianie nowego wystąpienia za pomocą pojedynczej pary formatu danych/danych. <xref:System.Windows.DataObject>  
  
 Poniższy przykładowy kod tworzy nowy obiekt danych i używa jednego z przeciążonych konstruktorów <xref:System.Windows.DataObject.%23ctor%2A>(<xref:System.Windows.DataObject.%23ctor(System.String,System.Object)>) w celu zainicjowania obiektu danych z ciągiem i określonym formatem danych.  W takim przypadku format danych jest określany przez ciąg; <xref:System.Windows.DataFormats> Klasa zawiera zestaw wstępnie zdefiniowanych ciągów typu. Funkcja autokonwersji przechowywanych danych jest domyślnie dozwolona.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
 Aby uzyskać więcej przykładów kodu, który tworzy obiekt danych, zobacz [Tworzenie obiektu danych](how-to-create-a-data-object.md).  
  
### <a name="storing-data-in-multiple-formats"></a>Przechowywanie danych w wielu formatach  
 Pojedynczy obiekt danych może przechowywać dane w wielu formatach.   Strategiczne użycie wielu formatów danych w ramach jednego obiektu danych potencjalnie może sprawiać, że obiekt danych jest przydatny przez szersze dużo obiektów docelowych, niż w przypadku, gdy tylko jeden format danych mógłby być reprezentowany.  Należy pamiętać, że ogólnie rzecz biorąc, Źródło przeciągania musi być niezależny od o formaty danych, które są używane przez potencjalną tarczę upuszczania.  
  
 Poniższy przykład pokazuje, <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> jak używać metody do dodawania danych do obiektu danych w wielu formatach.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
### <a name="querying-a-data-object-for-available-formats"></a>Wykonywanie zapytania dotyczącego obiektu danych dla dostępnych formatów  
 Ponieważ pojedynczy obiekt danych może zawierać dowolną liczbę formatów danych, obiekty danych obejmują funkcje do pobierania listy dostępnych formatów danych.  
  
 Poniższy przykładowy kod używa przeciążenia, <xref:System.Windows.DataObject.GetFormats%2A> aby pobrać tablicę ciągów wskazujących wszystkie formaty danych dostępne w obiekcie danych (zarówno natywne, jak i przez funkcję autokonwersji).  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
 Aby uzyskać więcej przykładów kodu, który wysyła zapytanie do obiektu danych dla dostępnych formatów danych, zobacz [lista formatów danych w obiekcie danych](how-to-list-the-data-formats-in-a-data-object.md).  Przykłady wykonywania zapytań względem obiektu danych dla obecności określonego formatu danych można znaleźć [w temacie Określanie, czy format danych jest obecny w obiekcie danych](how-to-determine-if-a-data-format-is-present-in-a-data-object.md).  
  
### <a name="retrieving-data-from-a-data-object"></a>Pobieranie danych z obiektu danych  
 Pobieranie danych z obiektu danych w określonym formacie wystarczy po prostu wywołać jedną z <xref:System.Windows.DataObject.GetData%2A> metod i określić żądany format danych.  Jedną z <xref:System.Windows.DataObject.GetDataPresent%2A> metod można użyć do sprawdzenia obecności określonego formatu danych.  <xref:System.Windows.DataObject.GetData%2A>zwraca dane w <xref:System.Object>. w zależności od formatu danych ten obiekt może być rzutowany do kontenera określonego typu.  
  
 Poniższy przykładowy kod używa przeciążenia, <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> aby sprawdzić, czy określony format danych jest dostępny (natywny lub przez funkcję autokonwersji). Jeśli określony format jest dostępny, przykład pobiera dane przy użyciu <xref:System.Windows.DataObject.GetData%28System.String%29> metody.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
 Aby uzyskać więcej przykładów kodu, który pobiera dane z obiektu danych, zobacz [pobieranie danych w określonym formacie danych](how-to-retrieve-data-in-a-particular-data-format.md).  
  
### <a name="removing-data-from-a-data-object"></a>Usuwanie danych z obiektu danych  
 Nie można bezpośrednio usunąć danych z obiektu danych.  Aby skutecznie usunąć dane z obiektu danych, wykonaj następujące kroki:  
  
1. Utwórz nowy obiekt danych, który będzie zawierać tylko dane, które chcesz zachować.  
  
2. "Skopiuj" wymagane dane ze starego obiektu danych do nowego obiektu danych.  Aby skopiować dane, użyj jednej z <xref:System.Windows.DataObject.GetData%2A> metod do <xref:System.Object> pobrania, która zawiera dane pierwotne, a <xref:System.Windows.DataObject.SetData%2A> następnie użyj jednej z metod, aby dodać dane do nowego obiektu danych.  
  
3. Zastąp stary obiekt danych nowym.  
  
> [!NOTE]
> <xref:System.Windows.DataObject.SetData%2A> Metody służą tylko do dodawania danych do obiektu danych. nie zastępują danych, nawet jeśli dane i format danych są dokładnie takie same jak w poprzednim wywołaniu. Dwukrotne wywołanie <xref:System.Windows.DataObject.SetData%2A> tych samych danych i formatu danych spowoduje, że format danych/danych zostanie zaprezentowany dwa razy w obiekcie danych.
