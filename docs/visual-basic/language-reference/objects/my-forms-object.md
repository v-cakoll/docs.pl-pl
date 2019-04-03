---
title: My.Forms — obiekt (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: 4998097b910a504461a34af3cc159ddb1c74cc62
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832557"
---
# <a name="myforms-object"></a>My.Forms — Obiekt
Udostępnia właściwości do uzyskiwania dostępu do wystąpienia każdego formularza Windows zadeklarowana w bieżącym projekcie.  
  
## <a name="remarks"></a>Uwagi  
 `My.Forms` Obiekt zawiera wystąpienie każdego formularza w bieżącym projekcie. Nazwa właściwości jest taka sama jak nazwa formularza, który uzyskuje dostęp do właściwości.   
  
 Możesz uzyskać dostęp przypominają zwykłe formularze `My.Forms` obiektu przy użyciu nazwy formularza, bez kwalifikacji. Nazwa właściwości jest taka sama jak nazwa typu formularza, to umożliwia dostęp do formularza tak, jakby był domyślnego wystąpienia. Na przykład `My.Forms.Form1.Show` jest odpowiednikiem `Form1.Show`.  
  
 `My.Forms` Obiekt udostępnia tylko formularze, które są skojarzone z bieżącego projektu. Go nie zapewnia dostępu do formularzy zadeklarowane w przywoływanych bibliotekach DLL. Aby uzyskać dostęp do formularza, który zawiera biblioteki DLL, należy użyć kwalifikowana nazwa formularza zapisywane jako *Nazwa_pliku_dll*. *Nazwa_formularza*.  
  
 Możesz użyć <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> właściwości do pobrania zbiór wszystkich aplikacji, otwartych formularzy.  
  
 Obiekt i jego właściwości są dostępne tylko dla aplikacji Windows.  
  
## <a name="properties"></a>Właściwości  
 Każda właściwość `My.Forms` obiekt umożliwia dostęp do wystąpienia do formularza w bieżącym projekcie. Nazwa właściwości jest taka sama jak nazwa formularza, który uzyskuje dostęp do właściwości, a typ właściwości jest taka sama jak typ formularza.  
  
> [!NOTE]
>  W przypadku kolizji nazw, nazwę właściwości, aby przejść do formularza jest *RootNamespace*_*Namespace*\_*Nazwa_formularza*. Na przykład, należy wziąć pod uwagę dwie formy o nazwie `Form1.`jednej z poniższych metod czy w głównej przestrzeni nazw `WindowsApplication1` w przestrzeni nazw `Namespace1`, dostęp do formularza przy użyciu `My.Forms.WindowsApplication1_Namespace1_Form1`.  
  
 `My.Forms` Obiekt umożliwia dostęp do wystąpienia aplikacji formularza głównego, który został utworzony podczas uruchamiania. Dla wszystkich innych form `My.Forms` obiektu tworzy nowe wystąpienie formularza, jeśli jest dostępny i zapisuje go. Kolejne próby dostępu do tej właściwości zwracają tego wystąpienia formularza.  
  
 Można dysponować formularza, przypisując `Nothing` do właściwości dla formularza. Wywołania metody ustawiającej właściwość <xref:System.Windows.Forms.Form.Close%2A> metody formularza, a następnie przypisuje `Nothing` do przechowywanej wartości. Jeśli przypiszesz dowolnej wartości innych niż `Nothing` dla właściwości, metody ustawiającej zgłasza <xref:System.ArgumentException> wyjątku.  
  
 Możesz sprawdzić, czy właściwość `My.Forms` obiekt przechowuje wystąpienia formularza za pomocą `Is` lub `IsNot` operatora. Aby sprawdzić, czy wartość właściwości można używać tych operatorów `Nothing`.  
  
> [!NOTE]
>  Zazwyczaj `Is` lub `IsNot` operator ma zostać odczytana wartość właściwości, które ma wykonać porównanie. Jednakże jeśli właściwość jest obecnie przechowuje `Nothing`, właściwość tworzy nowe wystąpienie formularza, a następnie zwraca tego wystąpienia. Jednak kompilator języka Visual Basic traktuje właściwości `My.Forms` obiektu inaczej i umożliwia `Is` lub `IsNot` operatora, aby sprawdzić stan właściwości bez zmieniania jego wartości.  
  
## <a name="example"></a>Przykład  
 Ten przykład umożliwia zmianę tytuł domyślnego `SidebarMenu` formularza.  
  
 [!code-vb[VbVbalrMyForms#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyForms/VB/Class1.vb#2)]  
  
 W tym przykładzie do pracy, projekt musi mieć formularz o nazwie `SidebarMenu`.  
  
 Ten kod będzie działać tylko w projekcie aplikacji Windows.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="availability-by-project-type"></a>Dostępność według typu projektu  
  
|Typ projektu|Dostępne|  
|---|---|  
|Aplikacja Windows|**Tak**|  
|Biblioteka klas|Nie|  
|Aplikacja konsoli|Nie|  
|Biblioteka formantów Windows|Nie|  
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
