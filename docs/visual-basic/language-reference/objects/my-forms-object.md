---
title: My.Forms — Obiekt
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: 4d6bb371b13dfb3fb735223b2a6a6a35e1416593
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="myforms-object"></a>My.Forms — Obiekt
Dostarcza właściwości, aby uzyskać dostęp do wystąpienia każdego formularza systemu Windows zadeklarowana w bieżącym projekcie.  
  
## <a name="remarks"></a>Uwagi  
 `My.Forms` Obiektu zawiera wystąpienie każdego formularza w bieżącym projekcie. Nazwa właściwości jest taka sama jak nazwa formularza, który uzyskuje dostęp do właściwości.   
  
 Dostęp można uzyskać formularzy dostarczonych przez `My.Forms` obiektu przy użyciu nazwy w postaci bez kwalifikacji. Nazwa właściwości jest taka sama jak nazwa typu formularza, to umożliwia dostęp do formularza tak, jakby zawierał wystąpienia domyślnego. Na przykład `My.Forms.Form1.Show` jest odpowiednikiem `Form1.Show`.  
  
 `My.Forms` Obiekt ujawnia tylko do formularzy, które są skojarzone z bieżącego projektu. Nie ma dostępu do formularzy zadeklarowany w przywoływane biblioteki dll. Aby uzyskać dostęp do formularza, który udostępnia bibliotekę DLL, należy użyć nazwa kwalifikowana w postaci zapisywane jako *DllName*. *Nazwa formularza*.  
  
 Można użyć <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> właściwości do pobrania kolekcja formularzy otwartych wszystkich aplikacji.  
  
 Obiekt i jego właściwości są dostępne tylko dla aplikacji systemu Windows.  
  
## <a name="properties"></a>Właściwości  
 Każda właściwość `My.Forms` obiektu zapewnia dostęp do wystąpienia formularza w bieżącym projekcie. Nazwa właściwości jest taka sama jak nazwa formularza, który uzyskuje dostęp do właściwości, a typ właściwości jest taki sam jak typ formularza.  
  
> [!NOTE]
>  W przypadku kolizję nazw, nazwę właściwości, aby przejść do formularza jest *RootNamespace*_*Namespace*\_*nazwa formularza*. Rozważmy na przykład dwie formy o nazwie `Form1.`Jeśli jeden z nich jest w głównej przestrzeni nazw `WindowsApplication1` i w przestrzeni nazw `Namespace1`, czy dostęp do tego formularza za pomocą `My.Forms.WindowsApplication1_Namespace1_Form1`.  
  
 `My.Forms` Obiekt zapewnia dostęp do wystąpienia aplikacji formularz główny, który został utworzony podczas uruchamiania. Dla wszystkich innych formularzy `My.Forms` obiektu tworzy nowe wystąpienie formularza, gdy jest dostępny i zapisuje go. Kolejne próby dostęp do tej właściwości zwrócenie tego wystąpienia formularza.  
  
 Można zlikwidować formularza, przypisując `Nothing` do właściwości dla tego formularza. Wywołania metody ustawiającej właściwość <xref:System.Windows.Forms.Form.Close%2A> metody formularza, a następnie przypisuje `Nothing` przechowywanej wartości. Po przypisaniu wartości inne niż `Nothing` do właściwości metody ustawiającej zgłasza <xref:System.ArgumentException> wyjątku.  
  
 Można sprawdzić, czy właściwość `My.Forms` obiekt przechowuje wystąpienia formularza za pomocą `Is` lub `IsNot` operatora. Te operatory można użyć do sprawdzenia, czy wartość właściwości jest `Nothing`.  
  
> [!NOTE]
>  Zazwyczaj `Is` lub `IsNot` operator ma odczytać wartości właściwości do porównania. Jednak jeśli właściwość obecnie przechowuje `Nothing`, właściwość tworzy nowe wystąpienie formularza, a następnie zwraca tego wystąpienia. Jednak kompilator Visual Basic traktuje właściwości `My.Forms` obiektu inaczej i umożliwia `Is` lub `IsNot` operatora, aby sprawdzić stan właściwości bez zmiany jego wartość.  
  
## <a name="example"></a>Przykład  
 Ten przykład umożliwia zmianę nazwy domyślnej `SidebarMenu` formularza.  
  
 [!code-vb[VbVbalrMyForms#2](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-forms-object_1.vb)]  
  
 Na przykład do pracy projektu musi mieć formularza o nazwie `SidebarMenu`.  
  
 Ten kod będzie działać tylko w projekcie aplikacji systemu Windows.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="availability-by-project-type"></a>Dostępność według typu projektu  
  
|Typ projektu|Dostępne|  
|---|---|  
|Aplikacja systemu Windows|**Tak**|  
|Biblioteka klas|Nie|  
|Aplikacja konsoli|Nie|  
|Biblioteka formantów systemu Windows|Nie|  
|Biblioteka formantów sieci Web|Nie|  
|Usługa systemu Windows|Nie|  
|Witryna sieci Web|Nie|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.Windows.Forms.Form.Close%2A>  
 [Obiekty](../../../visual-basic/language-reference/objects/index.md)  
 [Is, operator](../../../visual-basic/language-reference/operators/is-operator.md)  
 [IsNot, operator](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [Uzyskiwanie dostępu do formularzy aplikacji](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
