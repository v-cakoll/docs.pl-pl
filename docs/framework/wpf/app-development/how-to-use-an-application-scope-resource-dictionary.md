---
title: "Jak użyć słownika zasobów zakresu aplikacji"
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
- dictionaries [WPF], resource
- resource dictionaries [WPF], application-scope
- application-scope resource dictionaries
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 04dbcfb0fa16ceb4d6778ef611e926894d7840e9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a><span data-ttu-id="ea16e-102">Jak użyć słownika zasobów zakresu aplikacji</span><span class="sxs-lookup"><span data-stu-id="ea16e-102">How to: Use an Application-Scope Resource Dictionary</span></span>
<span data-ttu-id="ea16e-103">Ten przykład przedstawia sposób definiowania i użyć słownika zasobów niestandardowych zakresu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ea16e-103">This example shows how to define and use an application-scope custom resource dictionary.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea16e-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="ea16e-104">Example</span></span>  
 <span data-ttu-id="ea16e-105"><xref:System.Windows.Application>udostępnia magazyn zakresu aplikacji do zasobów udostępnionych: <xref:System.Windows.Application.Resources%2A>.</span><span class="sxs-lookup"><span data-stu-id="ea16e-105"><xref:System.Windows.Application> exposes an application-scope store for shared resources: <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="ea16e-106">Domyślnie <xref:System.Windows.Application.Resources%2A> właściwość jest inicjowana przy użyciu wystąpienia <xref:System.Windows.ResourceDictionary> typu.</span><span class="sxs-lookup"><span data-stu-id="ea16e-106">By default, the <xref:System.Windows.Application.Resources%2A> property is initialized with an instance of the <xref:System.Windows.ResourceDictionary> type.</span></span> <span data-ttu-id="ea16e-107">Użyj tego wystąpienia, gdy get i set właściwości zakresu aplikacji za pomocą <xref:System.Windows.Application.Resources%2A>.</span><span class="sxs-lookup"><span data-stu-id="ea16e-107">You use this instance when you get and set application-scope properties using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="ea16e-108">Aby uzyskać więcej informacji, zobacz [porady: pobieranie i Ustawianie zakresu aplikacji zasobów](http://msdn.microsoft.com/library/39e0420c-c9fc-47dc-8956-fdd95b214095).</span><span class="sxs-lookup"><span data-stu-id="ea16e-108">For more information, see [How to: Get and Set an Application-Scope Resource](http://msdn.microsoft.com/library/39e0420c-c9fc-47dc-8956-fdd95b214095).</span></span>
  
 <span data-ttu-id="ea16e-109">Jeśli masz wiele zasobów, które można ustawić za pomocą <xref:System.Windows.Application.Resources%2A>, można zamiast tego użyć słownika zasobów niestandardowych do przechowywania tych zasobów i ustawić <xref:System.Windows.Application.Resources%2A> z nim zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="ea16e-109">If you have multiple resources that you set using <xref:System.Windows.Application.Resources%2A>, you can instead use a custom resource dictionary to store those resources and set <xref:System.Windows.Application.Resources%2A> with it instead.</span></span> <span data-ttu-id="ea16e-110">Poniżej przedstawiono, jak zadeklarować słownik zasobów niestandardowych przy użyciu kodu XAML.</span><span class="sxs-lookup"><span data-stu-id="ea16e-110">The following shows how you declare a custom resource dictionary using XAML.</span></span>
  
 [!code-xaml[HOWTOResourceDictionaries#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 <span data-ttu-id="ea16e-111">Zamiana słowniki zasobów całej przy użyciu <xref:System.Windows.Application.Resources%2A> służy do obsługi motywów zakres aplikacji, gdzie każdy motyw jest hermetyzowany za słownika pojedynczego zasobu.</span><span class="sxs-lookup"><span data-stu-id="ea16e-111">Swapping entire resource dictionaries using <xref:System.Windows.Application.Resources%2A> allows you to support application-scope themes, where each theme is encapsulated by a single resource dictionary.</span></span> <span data-ttu-id="ea16e-112">Poniższy przykład przedstawia sposób ustawiania <xref:System.Windows.ResourceDictionary>.</span><span class="sxs-lookup"><span data-stu-id="ea16e-112">The following example shows how to set the <xref:System.Windows.ResourceDictionary>.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 <span data-ttu-id="ea16e-113">Poniżej pokazano, jak można pobrać zasobów zakresu aplikacji ze słownika zasobów udostępnianych przez <xref:System.Windows.Application.Resources%2A> w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="ea16e-113">The following shows how you can get application-scope resources from the resource dictionary exposed by <xref:System.Windows.Application.Resources%2A> in XAML.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 <span data-ttu-id="ea16e-114">Poniżej przedstawiono, jak również można uzyskać zasoby w kodzie.</span><span class="sxs-lookup"><span data-stu-id="ea16e-114">The following shows how you can also get the resources in code.</span></span>  
  
 [!code-csharp[HOWTOResourceDictionaries#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 <span data-ttu-id="ea16e-115">Istnieją dwa zagadnienia dotyczące podczas korzystania z <xref:System.Windows.Application.Resources%2A>.</span><span class="sxs-lookup"><span data-stu-id="ea16e-115">There are two considerations to make when using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="ea16e-116">Po pierwsze, słownik *klucza* jest obiektem, dlatego należy użyć dokładnie tego samego wystąpienia obiektu podczas zarówno ustawiania i pobierania wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="ea16e-116">First, the dictionary *key* is an object, so you must use exactly the same object instance when both setting and getting a property value.</span></span> <span data-ttu-id="ea16e-117">(Należy zwrócić uwagę, czy klucz jest rozróżniana wielkość liter, korzystając z ciągu). Drugi, słownik *wartość* jest obiektem, dlatego należy przekonwertować wartości na żądany typ. podczas pobierania wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="ea16e-117">(Note that the key is case-sensitive when using a string.) Second, the dictionary *value* is an object, so you will have to convert the value to the desired type when getting a property value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea16e-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ea16e-118">See Also</span></span>  
 <xref:System.Windows.ResourceDictionary>  
 <xref:System.Windows.Application.Resources%2A>  
 [<span data-ttu-id="ea16e-119">Zasoby XAML</span><span class="sxs-lookup"><span data-stu-id="ea16e-119">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="ea16e-120">Połączone słowniki zasobów</span><span class="sxs-lookup"><span data-stu-id="ea16e-120">Merged Resource Dictionaries</span></span>](../../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md)
