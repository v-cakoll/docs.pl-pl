---
title: My. Forms — obiekt (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: 9a0b3b9202972122aea4a7147d8d872486418264
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581867"
---
# <a name="myforms-object"></a>My.Forms — Obiekt

Zawiera właściwości umożliwiające dostęp do wystąpienia każdego formularza systemu Windows zadeklarowanego w bieżącym projekcie.

## <a name="remarks"></a>Uwagi

Obiekt `My.Forms` zawiera wystąpienie każdego formularza w bieżącym projekcie. Nazwa właściwości jest taka sama jak nazwa formularza, do którego uzyskuje dostęp właściwość.

Dostęp do formularzy dostarczonych przez obiekt `My.Forms` można uzyskać przy użyciu nazwy formularza bez kwalifikacji. Ponieważ nazwa właściwości jest taka sama jak nazwa typu formularza, pozwala to na dostęp do formularza tak, jakby miał wystąpienie domyślne. Na przykład `My.Forms.Form1.Show` jest równoznaczne z `Form1.Show`.

Obiekt `My.Forms` uwidacznia tylko formularze skojarzone z bieżącym projektem. Nie zapewnia dostępu do formularzy zadeklarowanych w przywoływanych bibliotekach DLL. Aby uzyskać dostęp do formularza, który zapewnia Biblioteka DLL, należy użyć kwalifikowanej nazwy formularza, która jest zapisywana jako *nazwa_pliku_dll*. *FormatName*.

Możesz użyć właściwości <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>, aby uzyskać kolekcję wszystkich otwartych formularzy aplikacji.

Obiekt i jego właściwości są dostępne tylko dla aplikacji systemu Windows.

## <a name="properties"></a>Właściwości

Każda właściwość obiektu `My.Forms` zapewnia dostęp do wystąpienia formularza w bieżącym projekcie. Nazwa właściwości jest taka sama jak nazwa formularza, do którego uzyskuje dostęp właściwość, a typ właściwości jest taki sam jak typ formularza.

> [!NOTE]
> W przypadku kolizji nazw nazwa właściwości do uzyskiwania dostępu do formularza to *RootNamespace*_*przestrzeń nazw* \_*FormName*. Rozważmy na przykład dwa formularze o nazwie `Form1.`If jeden z tych formularzy znajduje się w głównej przestrzeni nazw `WindowsApplication1` i w `Namespace1` przestrzeni nazw, można uzyskać dostęp do tego formularza za pomocą `My.Forms.WindowsApplication1_Namespace1_Form1`.

Obiekt `My.Forms` zapewnia dostęp do wystąpienia głównego formularza aplikacji, który został utworzony podczas uruchamiania. W przypadku wszystkich innych formularzy obiekt `My.Forms` tworzy nowe wystąpienie formularza, gdy jest on dostępny i zapisuje je. Kolejne próby uzyskania dostępu do tej właściwości zwracają to wystąpienie formularza.

Można usunąć formularz, przypisując `Nothing` do właściwości dla tego formularza. Metoda ustawiająca właściwość wywołuje metodę <xref:System.Windows.Forms.Form.Close%2A> formularza, a następnie przypisuje `Nothing` do przechowywanej wartości. Jeśli przypiszesz dowolną wartość inną niż `Nothing` do właściwości, Metoda ustawiająca zgłosi wyjątek <xref:System.ArgumentException>.

Można sprawdzić, czy właściwość obiektu `My.Forms` przechowuje wystąpienie formularza przy użyciu operatora `Is` lub `IsNot`. Można użyć tych operatorów do sprawdzenia, czy wartość właściwości jest `Nothing`.

> [!NOTE]
> Zazwyczaj operator `Is` lub `IsNot` musi odczytywać wartość właściwości w celu przeprowadzenia porównania. Jeśli jednak Właściwość aktualnie przechowuje `Nothing`, Właściwość tworzy nowe wystąpienie formularza, a następnie zwraca to wystąpienie. Jednak kompilator Visual Basic traktuje właściwości obiektu `My.Forms` inaczej i umożliwi operatorowi `Is` lub `IsNot` sprawdzenie stanu właściwości bez zmiany jej wartości.

## <a name="example"></a>Przykład

Ten przykład zmienia tytuł domyślnego formularza `SidebarMenu`.

[!code-vb[VbVbalrMyForms#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyForms/VB/Class1.vb#2)]

Aby ten przykład działał, projekt musi mieć formularz o nazwie `SidebarMenu`.

Ten kod będzie działał tylko w projekcie aplikacji systemu Windows.

## <a name="requirements"></a>Wymagania

### <a name="availability-by-project-type"></a>Dostępność według typu projektu

|Typ projektu|Dostępne|
|---|---|
|Aplikacja systemu Windows|**Opcję**|
|Biblioteka klas|Nie|
|Aplikacja konsoli|Nie|
|Biblioteka formantów systemu Windows|Nie|
|Biblioteka formantów sieci Web|Nie|
|Usługa systemu Windows|Nie|
|Witryna sieci Web|Nie|

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Form.Close%2A>
- [Obiekty](../../../visual-basic/language-reference/objects/index.md)
- [Is, operator](../../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot, operator](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Uzyskiwanie dostępu do formularzy aplikacji](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
