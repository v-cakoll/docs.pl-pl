---
title: 'Porady: wywoływanie powiadomień o zmianie za pomocą składnika BindingSource i interfejsu INotifyPropertyChanged'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- change notifications [Windows Forms], raising
- BindingSource component [Windows Forms], and IPropertyChange
- data sources [Windows Forms], detecting changes
- examples [Windows Forms], BindingSource component
- change notifications
- INotifyPropertyChanged interface [Windows Forms], using with BindingSource
- BindingSource component [Windows Forms], examples
ms.assetid: 7fa2cf51-c09f-4375-adf0-e36c5617f099
ms.openlocfilehash: 2fe4458aa43144a9c29ed67fd7bee99a37fe1434
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739684"
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a><span data-ttu-id="4b5c6-102">Porady: wywoływanie powiadomień o zmianie za pomocą składnika BindingSource i interfejsu INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="4b5c6-102">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="4b5c6-103">Składnik <xref:System.Windows.Forms.BindingSource> automatycznie wykrywa zmiany w źródle danych, gdy typ zawarty w <xref:System.ComponentModel.INotifyPropertyChanged> źródle <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> danych implementuje i wywołuje zdarzenia po zmianie wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="4b5c6-103">The <xref:System.Windows.Forms.BindingSource> component automatically detects changes in a data source when the type contained in the data source implements <xref:System.ComponentModel.INotifyPropertyChanged> and raises <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> events when a property value is changed.</span></span> <span data-ttu-id="4b5c6-104">To wykrywanie zmian jest przydatne, ponieważ formanty powiązane z automatyczną aktualizacją <xref:System.Windows.Forms.BindingSource> w miarę zmiany wartości źródła danych.</span><span class="sxs-lookup"><span data-stu-id="4b5c6-104">This change detection is useful because controls bound to the <xref:System.Windows.Forms.BindingSource> automatically update as the data source values change.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4b5c6-105">Jeśli źródło danych <xref:System.ComponentModel.INotifyPropertyChanged> implementuje i wykonujesz operacje asynchroniczne, nie należy wprowadzać zmian w źródle danych w wątku w tle.</span><span class="sxs-lookup"><span data-stu-id="4b5c6-105">If your data source implements <xref:System.ComponentModel.INotifyPropertyChanged> and you are performing asynchronous operations, you should not make changes to the data source on a background thread.</span></span> <span data-ttu-id="4b5c6-106">Zamiast tego należy odczytać dane w wątku w tle i scalić dane do listy w wątku interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4b5c6-106">Instead, you should read the data on a background thread and merge the data into a list on the UI thread.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b5c6-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="4b5c6-107">Example</span></span>  
 <span data-ttu-id="4b5c6-108">Poniższy przykład kodu pokazuje prostą <xref:System.ComponentModel.INotifyPropertyChanged> implementację interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4b5c6-108">The following code example demonstrates a simple implementation of the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="4b5c6-109">Pokazuje również, <xref:System.Windows.Forms.BindingSource> jak automatycznie przekazuje zmiany źródła danych do <xref:System.Windows.Forms.BindingSource> kontroli powiązanej, <xref:System.ComponentModel.INotifyPropertyChanged> gdy jest powiązany z listą typu.</span><span class="sxs-lookup"><span data-stu-id="4b5c6-109">It also shows how the <xref:System.Windows.Forms.BindingSource> automatically passes a data source change to a bound control when the <xref:System.Windows.Forms.BindingSource> is bound to a list of the <xref:System.ComponentModel.INotifyPropertyChanged> type.</span></span>  
  
 <span data-ttu-id="4b5c6-110">Jeśli używasz `CallerMemberName` atrybutu, wywołania `NotifyPropertyChanged` metody nie trzeba określać nazwę właściwości jako argument ciągu.</span><span class="sxs-lookup"><span data-stu-id="4b5c6-110">If you use the `CallerMemberName` attribute, calls to the `NotifyPropertyChanged` method don't have to specify the property name as a string argument.</span></span> <span data-ttu-id="4b5c6-111">Aby uzyskać więcej informacji, zobacz [Informacje o dzwoniącym (C#)](../../../csharp/language-reference/attributes/caller-information.md) lub [Informacje o dzwoniącym (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="4b5c6-111">For more information, see [Caller Information (C#)](../../../csharp/language-reference/attributes/caller-information.md) or [Caller Information (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4b5c6-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="4b5c6-112">Compiling the Code</span></span>  
 <span data-ttu-id="4b5c6-113">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="4b5c6-113">This example requires:</span></span>  
  
- <span data-ttu-id="4b5c6-114">Odwołania do zestawów System, System.Data, System.Drawing i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="4b5c6-114">References to the System, System.Data, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b5c6-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4b5c6-115">See also</span></span>

- <xref:System.ComponentModel.INotifyPropertyChanged>
- [<span data-ttu-id="4b5c6-116">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="4b5c6-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="4b5c6-117">Instrukcje: wywoływanie powiadomień o zmianie za pomocą metody BindingSource ResetItem</span><span class="sxs-lookup"><span data-stu-id="4b5c6-117">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
