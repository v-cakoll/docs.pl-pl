---
title: My.Forms — Obiekt
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: 001f6fbfae2467ea0af5e98ca041b694d1e7b8f9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372443"
---
# <a name="myforms-object"></a>My.Forms — Obiekt

Zawiera właściwości umożliwiające dostęp do wystąpienia każdego formularza systemu Windows zadeklarowanego w bieżącym projekcie.

## <a name="remarks"></a>Uwagi

`My.Forms`Obiekt zawiera wystąpienie każdego formularza w bieżącym projekcie. Nazwa właściwości jest taka sama jak nazwa formularza, do którego uzyskuje dostęp właściwość.

Dostęp do formularzy dostarczonych przez obiekt można uzyskać `My.Forms` przy użyciu nazwy formularza bez kwalifikacji. Ponieważ nazwa właściwości jest taka sama jak nazwa typu formularza, pozwala to na dostęp do formularza tak, jakby miał wystąpienie domyślne. Na przykład `My.Forms.Form1.Show` jest równoważne `Form1.Show` .

`My.Forms`Obiekt uwidacznia tylko formularze skojarzone z bieżącym projektem. Nie zapewnia dostępu do formularzy zadeklarowanych w przywoływanych bibliotekach DLL. Aby uzyskać dostęp do formularza, który zapewnia Biblioteka DLL, należy użyć kwalifikowanej nazwy formularza, która jest zapisywana jako *nazwa_pliku_dll*. *FormatName*.

Możesz użyć właściwości, <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> Aby uzyskać kolekcję wszystkich otwartych formularzy aplikacji.

Obiekt i jego właściwości są dostępne tylko dla aplikacji systemu Windows.

## <a name="properties"></a>Właściwości

Każda właściwość `My.Forms` obiektu zapewnia dostęp do wystąpienia formularza w bieżącym projekcie. Nazwa właściwości jest taka sama jak nazwa formularza, do którego uzyskuje dostęp właściwość, a typ właściwości jest taki sam jak typ formularza.

> [!NOTE]
> W przypadku kolizji nazw nazwa właściwości do uzyskiwania dostępu do formularza to *RootNamespace*_*NamespaceName* \_ *FormName*. Rozważmy na przykład dwa formularze o nazwie, `Form1.` Jeśli jeden z tych formularzy znajduje się w głównej przestrzeni nazw `WindowsApplication1` i w przestrzeni nazw `Namespace1` , możesz uzyskać dostęp do tego formularza `My.Forms.WindowsApplication1_Namespace1_Form1` .

`My.Forms`Obiekt umożliwia dostęp do wystąpienia głównego formularza aplikacji, który został utworzony podczas uruchamiania. W przypadku wszystkich innych formularzy `My.Forms` obiekt tworzy nowe wystąpienie formularza, gdy jest on dostępny i przechowuje je. Kolejne próby uzyskania dostępu do tej właściwości zwracają to wystąpienie formularza.

Formularz można usunąć, przypisując `Nothing` do właściwości tego formularza. Metoda ustawiająca właściwość wywołuje <xref:System.Windows.Forms.Form.Close%2A> metodę formularza, a następnie przypisuje `Nothing` do przechowywanej wartości. Jeśli przypiszesz dowolną wartość inną niż `Nothing` Właściwość, Metoda ustawiająca zgłosi <xref:System.ArgumentException> wyjątek.

Można sprawdzić, czy właściwość `My.Forms` obiektu przechowuje wystąpienie formularza przy użyciu `Is` `IsNot` operatora OR. Można użyć tych operatorów do sprawdzenia, czy wartość właściwości jest `Nothing` .

> [!NOTE]
> Zazwyczaj `Is` `IsNot` operator or musi odczytywać wartość właściwości w celu przeprowadzenia porównania. Jeśli jednak właściwość jest obecnie przechowywana `Nothing` , Właściwość tworzy nowe wystąpienie formularza, a następnie zwraca to wystąpienie. Jednak kompilator Visual Basic traktuje właściwości `My.Forms` obiektu inaczej i umożliwia `Is` `IsNot` operatorowi or sprawdzenie stanu właściwości bez zmiany jego wartości.

## <a name="example"></a>Przykład

Ten przykład zmienia tytuł `SidebarMenu` formularza domyślnego.

[!code-vb[VbVbalrMyForms#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyForms/VB/Class1.vb#2)]

Aby ten przykład działał, projekt musi mieć formularz o nazwie `SidebarMenu` .

Ten kod będzie działał tylko w projekcie aplikacji systemu Windows.

## <a name="requirements"></a>Wymagania

### <a name="availability-by-project-type"></a>Dostępność według typu projektu

|Project type (Typ projektu)|Dostępne|
|---|---|
|Aplikacja systemu Windows|**Tak**|
|Biblioteka klas|Nie|
|Aplikacja konsoli|Nie|
|Biblioteka formantów systemu Windows|Nie|
|Biblioteka formantów sieci Web|Nie|
|Usługa systemu Windows|Nie|
|Witryna sieci Web|Nie|

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Form.Close%2A>
- [Obiekty](index.md)
- [Is, operator](../operators/is-operator.md)
- [IsNot, operator](../operators/isnot-operator.md)
- [Uzyskiwanie dostępu do formularzy aplikacji](../../developing-apps/programming/accessing-application-forms.md)
