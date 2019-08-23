---
title: 'Instrukcje: wywoływanie powiadomień o zmianie za pomocą składnika BindingSource i interfejsu INotifyPropertyChanged'
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
ms.openlocfilehash: 7dc640f272226da650a63b1a3434822d21053b48
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968284"
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a><span data-ttu-id="10b48-102">Instrukcje: wywoływanie powiadomień o zmianie za pomocą składnika BindingSource i interfejsu INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="10b48-102">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="10b48-103">Składnik automatycznie wykryje zmiany w źródle danych, gdy typ zawarty w źródle danych <xref:System.ComponentModel.INotifyPropertyChanged> implementuje interfejs i zgłasza <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> zdarzenia, gdy wartość właściwości zostanie zmieniona. <xref:System.Windows.Forms.BindingSource></span><span class="sxs-lookup"><span data-stu-id="10b48-103">The <xref:System.Windows.Forms.BindingSource> component will automatically detect changes in a data source when the type contained in the data source implements the <xref:System.ComponentModel.INotifyPropertyChanged> interface and raises <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> events when a property value is changed.</span></span> <span data-ttu-id="10b48-104">Jest to przydatne, ponieważ formanty powiązane z <xref:System.Windows.Forms.BindingSource> , zostaną następnie automatycznie zaktualizowane w miarę zmiany wartości źródła danych.</span><span class="sxs-lookup"><span data-stu-id="10b48-104">This is useful because controls bound to the <xref:System.Windows.Forms.BindingSource> will then automatically update as the data source values change.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="10b48-105">Jeśli źródło danych implementuje <xref:System.ComponentModel.INotifyPropertyChanged> i wykonujesz operacje asynchroniczne, nie należy wprowadzać zmian w źródle danych w wątku w tle.</span><span class="sxs-lookup"><span data-stu-id="10b48-105">If your data source implements <xref:System.ComponentModel.INotifyPropertyChanged> and you are performing asynchronous operations, you should not make changes to the data source on a background thread.</span></span> <span data-ttu-id="10b48-106">Zamiast tego należy odczytywać dane w wątku w tle i scalać dane do listy w wątku interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="10b48-106">Instead, you should read the data on a background thread and merge the data into a list on the UI thread.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10b48-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="10b48-107">Example</span></span>  
 <span data-ttu-id="10b48-108">Poniższy przykład kodu demonstruje prostą implementację <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="10b48-108">The following code example demonstrates a simple implementation of the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="10b48-109">Pokazuje również, <xref:System.Windows.Forms.BindingSource> jak automatycznie przekazuje źródło danych do kontrolki powiązanej, <xref:System.Windows.Forms.BindingSource> gdy jest powiązany <xref:System.ComponentModel.INotifyPropertyChanged> z listą typu.</span><span class="sxs-lookup"><span data-stu-id="10b48-109">It also shows how the <xref:System.Windows.Forms.BindingSource> automatically passes a data source change to a bound control when the <xref:System.Windows.Forms.BindingSource> is bound to a list of the <xref:System.ComponentModel.INotifyPropertyChanged> type.</span></span>  
  
 <span data-ttu-id="10b48-110">Jeśli używasz `CallerMemberName` atrybutu, wywołania `NotifyPropertyChanged` do metody nie muszą określać nazwy właściwości jako argumentu ciągu.</span><span class="sxs-lookup"><span data-stu-id="10b48-110">If you use the `CallerMemberName` attribute, calls to the `NotifyPropertyChanged` method don't have to specify the property name as a string argument.</span></span> <span data-ttu-id="10b48-111">Aby uzyskać więcej informacji, zobacz [Informacje oC#wywołującym ()](../../../csharp/programming-guide/concepts/caller-information.md) lub [Informacje o wywołującym (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="10b48-111">For more information, see [Caller Information (C#)](../../../csharp/programming-guide/concepts/caller-information.md) or [Caller Information (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="10b48-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="10b48-112">Compiling the Code</span></span>  
 <span data-ttu-id="10b48-113">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="10b48-113">This example requires:</span></span>  
  
- <span data-ttu-id="10b48-114">Odwołania do zestawów system, system. Data, system. Drawing i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="10b48-114">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10b48-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="10b48-115">See also</span></span>

- <xref:System.ComponentModel.INotifyPropertyChanged>
- [<span data-ttu-id="10b48-116">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="10b48-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="10b48-117">Instrukcje: Zgłoś powiadomienia o zmianie za pomocą metody BindingSource ResetItem</span><span class="sxs-lookup"><span data-stu-id="10b48-117">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
