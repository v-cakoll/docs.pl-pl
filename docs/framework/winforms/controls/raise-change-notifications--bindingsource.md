---
title: "Porady: wywoływanie powiadomień o zmianie za pomocą składnika BindingSource i interfejsu INotifyPropertyChanged"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 049d87799e4ef241de0647815470cc853a29ea31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a><span data-ttu-id="9b894-102">Porady: wywoływanie powiadomień o zmianie za pomocą składnika BindingSource i interfejsu INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="9b894-102">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="9b894-103"><xref:System.Windows.Forms.BindingSource> Składnika będzie automatycznie wykrywał zmiany w źródle danych typu znajdujące się w implementuje źródła danych <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu i zgłasza <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> zdarzeń, gdy wartość właściwości zostanie zmieniona.</span><span class="sxs-lookup"><span data-stu-id="9b894-103">The <xref:System.Windows.Forms.BindingSource> component will automatically detect changes in a data source when the type contained in the data source implements the <xref:System.ComponentModel.INotifyPropertyChanged> interface and raises <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> events when a property value is changed.</span></span> <span data-ttu-id="9b894-104">Jest to przydatne, ponieważ formanty powiązane z <xref:System.Windows.Forms.BindingSource> następnie automatycznie zaktualizuje jako zmiana wartości źródła danych.</span><span class="sxs-lookup"><span data-stu-id="9b894-104">This is useful because controls bound to the <xref:System.Windows.Forms.BindingSource> will then automatically update as the data source values change.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b894-105">Jeśli źródło danych implementuje <xref:System.ComponentModel.INotifyPropertyChanged> i wykonują operacje asynchroniczne, nie należy wprowadzać zmian do źródła danych na wątku w tle.</span><span class="sxs-lookup"><span data-stu-id="9b894-105">If your data source implements <xref:System.ComponentModel.INotifyPropertyChanged> and you are performing asynchronous operations, you should not make changes to the data source on a background thread.</span></span> <span data-ttu-id="9b894-106">Należy odczytać danych z wątku w tle i Scal dane na liście w wątku interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9b894-106">Instead, you should read the data on a background thread and merge the data into a list on the UI thread.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b894-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="9b894-107">Example</span></span>  
 <span data-ttu-id="9b894-108">W poniższym przykładzie kodu pokazano prosty implementacja <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="9b894-108">The following code example demonstrates a simple implementation of the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="9b894-109">Zawiera także sposób <xref:System.Windows.Forms.BindingSource> automatycznie przekazuje zmian źródła danych do powiązanej decyduje o <xref:System.Windows.Forms.BindingSource> jest powiązany z listy <xref:System.ComponentModel.INotifyPropertyChanged> typu.</span><span class="sxs-lookup"><span data-stu-id="9b894-109">It also shows how the <xref:System.Windows.Forms.BindingSource> automatically passes a data source change to a bound control when the <xref:System.Windows.Forms.BindingSource> is bound to a list of the <xref:System.ComponentModel.INotifyPropertyChanged> type.</span></span>  
  
 <span data-ttu-id="9b894-110">Jeśli używasz `CallerMemberName` atrybutu, wywołania `NotifyPropertyChanged` metody nie trzeba określać nazwę właściwości jako argument ciągu.</span><span class="sxs-lookup"><span data-stu-id="9b894-110">If you use the `CallerMemberName` attribute, calls to the `NotifyPropertyChanged` method don't have to specify the property name as a string argument.</span></span> <span data-ttu-id="9b894-111">Aby uzyskać więcej informacji, zobacz [informacje o wywołującym](http://msdn.microsoft.com/library/9cb2b8c0-c4f6-44b8-9c90-38948455b373).</span><span class="sxs-lookup"><span data-stu-id="9b894-111">For more information, see [Caller Information](http://msdn.microsoft.com/library/9cb2b8c0-c4f6-44b8-9c90-38948455b373).</span></span>  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9b894-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="9b894-112">Compiling the Code</span></span>  
 <span data-ttu-id="9b894-113">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="9b894-113">This example requires:</span></span>  
  
-   <span data-ttu-id="9b894-114">Odwołania do zestawów systemu, dane systemowe, System.Drawing i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="9b894-114">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="9b894-115">Informacji dotyczących tworzenia tego przykładu z wiersza polecenia dla [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="9b894-115">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="9b894-116">Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="9b894-116">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="9b894-117">Zobacz też [HYPERLINK "http://msdn.microsoft.com/library/Bb129228 (v=vs.110)" porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="9b894-117">Also see [HYPERLINK "http://msdn.microsoft.com/library/Bb129228(v=vs.110)" How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b894-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9b894-118">See Also</span></span>  
 <xref:System.ComponentModel.INotifyPropertyChanged>  
 [<span data-ttu-id="9b894-119">BindingSource — składnik</span><span class="sxs-lookup"><span data-stu-id="9b894-119">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="9b894-120">Porady: wywoływanie powiadomień o zmianie za pomocą metody BindingSource Resetitem</span><span class="sxs-lookup"><span data-stu-id="9b894-120">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>](../../../../docs/framework/winforms/controls/how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
