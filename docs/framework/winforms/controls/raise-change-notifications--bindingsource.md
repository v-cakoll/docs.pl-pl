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
ms.openlocfilehash: 93949f003a55cdf67c4ecde988d268728c75e081
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614687"
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a><span data-ttu-id="8c278-102">Instrukcje: wywoływanie powiadomień o zmianie za pomocą składnika BindingSource i interfejsu INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="8c278-102">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="8c278-103"><xref:System.Windows.Forms.BindingSource> Składnika automatycznie wykryje zmiany w źródle danych, gdy typ zawarte w implementuje źródło danych <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu i zgłasza <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> zdarzenia po zmianie wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="8c278-103">The <xref:System.Windows.Forms.BindingSource> component will automatically detect changes in a data source when the type contained in the data source implements the <xref:System.ComponentModel.INotifyPropertyChanged> interface and raises <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> events when a property value is changed.</span></span> <span data-ttu-id="8c278-104">Jest to przydatne, ponieważ formanty powiązane z <xref:System.Windows.Forms.BindingSource> następnie automatycznie aktualizuje jak zmiana wartości źródła danych.</span><span class="sxs-lookup"><span data-stu-id="8c278-104">This is useful because controls bound to the <xref:System.Windows.Forms.BindingSource> will then automatically update as the data source values change.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8c278-105">Jeśli dane źródłowe implementuje <xref:System.ComponentModel.INotifyPropertyChanged> i wykonywania operacji asynchronicznych, nie powinna dokonywać zmian w źródle danych w wątku tła.</span><span class="sxs-lookup"><span data-stu-id="8c278-105">If your data source implements <xref:System.ComponentModel.INotifyPropertyChanged> and you are performing asynchronous operations, you should not make changes to the data source on a background thread.</span></span> <span data-ttu-id="8c278-106">Zamiast tego należy odczytać danych z wątku w tle i scalania danych na liście w wątku interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8c278-106">Instead, you should read the data on a background thread and merge the data into a list on the UI thread.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c278-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="8c278-107">Example</span></span>  
 <span data-ttu-id="8c278-108">Poniższy przykład kodu demonstruje proste wdrażanie <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="8c278-108">The following code example demonstrates a simple implementation of the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="8c278-109">Pokazuje także sposób, w jaki <xref:System.Windows.Forms.BindingSource> automatycznie przekazuje zmian źródła danych do granicy decyduje o <xref:System.Windows.Forms.BindingSource> jest powiązany z listy <xref:System.ComponentModel.INotifyPropertyChanged> typu.</span><span class="sxs-lookup"><span data-stu-id="8c278-109">It also shows how the <xref:System.Windows.Forms.BindingSource> automatically passes a data source change to a bound control when the <xref:System.Windows.Forms.BindingSource> is bound to a list of the <xref:System.ComponentModel.INotifyPropertyChanged> type.</span></span>  
  
 <span data-ttu-id="8c278-110">Jeśli używasz `CallerMemberName` atrybutu wywołania `NotifyPropertyChanged` metody nie trzeba określić nazwę właściwości jako argument ciągu.</span><span class="sxs-lookup"><span data-stu-id="8c278-110">If you use the `CallerMemberName` attribute, calls to the `NotifyPropertyChanged` method don't have to specify the property name as a string argument.</span></span> <span data-ttu-id="8c278-111">Aby uzyskać więcej informacji, zobacz [informacje o wywołującym (C#)](../../../csharp/programming-guide/concepts/caller-information.md) lub [informacje o wywołującym (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="8c278-111">For more information, see [Caller Information (C#)](../../../csharp/programming-guide/concepts/caller-information.md) or [Caller Information (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8c278-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="8c278-112">Compiling the Code</span></span>  
 <span data-ttu-id="8c278-113">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="8c278-113">This example requires:</span></span>  
  
- <span data-ttu-id="8c278-114">Odwołania do zestawów systemu, dane systemowe i System.Drawing oraz przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="8c278-114">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="8c278-115">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="8c278-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="8c278-116">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="8c278-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span> <span data-ttu-id="8c278-117">Zobacz też [jak: Skompilować i uruchomić przykładowy kod pełną Windows Forms przy użyciu programu Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb129228(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="8c278-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb129228(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c278-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c278-118">See also</span></span>

- <xref:System.ComponentModel.INotifyPropertyChanged>
- [<span data-ttu-id="8c278-119">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="8c278-119">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="8c278-120">Instrukcje: Wywoływanie powiadomień o zmianie za BindingSource Resetitem</span><span class="sxs-lookup"><span data-stu-id="8c278-120">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
