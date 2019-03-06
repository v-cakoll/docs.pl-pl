---
title: 'Instrukcje: Użyj słownika zasobów zakresu aplikacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dictionaries [WPF], resource
- resource dictionaries [WPF], application-scope
- application-scope resource dictionaries
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
ms.openlocfilehash: a2453ae7fad56205ae06835d8710ca126bba17c7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369737"
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a><span data-ttu-id="cea70-102">Instrukcje: Użyj słownika zasobów zakresu aplikacji</span><span class="sxs-lookup"><span data-stu-id="cea70-102">How to: Use an Application-Scope Resource Dictionary</span></span>
<span data-ttu-id="cea70-103">Ten przykład pokazuje, jak zdefiniować i użyć słownika niestandardowego zasobów zakresu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cea70-103">This example shows how to define and use an application-scope custom resource dictionary.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cea70-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="cea70-104">Example</span></span>  
 <span data-ttu-id="cea70-105"><xref:System.Windows.Application> udostępnia magazyn zakresu aplikacji do zasobów udostępnionych: <xref:System.Windows.Application.Resources%2A>.</span><span class="sxs-lookup"><span data-stu-id="cea70-105"><xref:System.Windows.Application> exposes an application-scope store for shared resources: <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="cea70-106">Domyślnie <xref:System.Windows.Application.Resources%2A> właściwość jest inicjowana z wystąpieniem <xref:System.Windows.ResourceDictionary> typu.</span><span class="sxs-lookup"><span data-stu-id="cea70-106">By default, the <xref:System.Windows.Application.Resources%2A> property is initialized with an instance of the <xref:System.Windows.ResourceDictionary> type.</span></span> <span data-ttu-id="cea70-107">Użycie tego wystąpienia, jeśli pobieranie i ustawianie właściwości zakresu aplikacji za pomocą <xref:System.Windows.Application.Resources%2A>.</span><span class="sxs-lookup"><span data-stu-id="cea70-107">You use this instance when you get and set application-scope properties using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="cea70-108">Aby uzyskać więcej informacji, zobacz [jak: Pobieranie i ustawianie zasobów zakresu aplikacji](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="cea70-108">For more information, see [How to: Get and Set an Application-Scope Resource](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100)).</span></span>
  
 <span data-ttu-id="cea70-109">Jeśli masz wiele zasobów, które można ustawić za pomocą <xref:System.Windows.Application.Resources%2A>, można zamiast tego użyć słownika zasobów niestandardowych do przechowywania tych zasobów i ustawić <xref:System.Windows.Application.Resources%2A> z nim zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="cea70-109">If you have multiple resources that you set using <xref:System.Windows.Application.Resources%2A>, you can instead use a custom resource dictionary to store those resources and set <xref:System.Windows.Application.Resources%2A> with it instead.</span></span> <span data-ttu-id="cea70-110">Poniżej przedstawiono, jak zadeklarować słownik zasobów niestandardowych przy użyciu XAML.</span><span class="sxs-lookup"><span data-stu-id="cea70-110">The following shows how you declare a custom resource dictionary using XAML.</span></span>
  
 [!code-xaml[HOWTOResourceDictionaries#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 <span data-ttu-id="cea70-111">Wymiana całego zasobu słownikami przy użyciu <xref:System.Windows.Application.Resources%2A> umożliwiają obsługę motywów zakres aplikacji, gdzie każdy motyw jest hermetyzowany przez słownik pojedynczy zasób.</span><span class="sxs-lookup"><span data-stu-id="cea70-111">Swapping entire resource dictionaries using <xref:System.Windows.Application.Resources%2A> allows you to support application-scope themes, where each theme is encapsulated by a single resource dictionary.</span></span> <span data-ttu-id="cea70-112">Poniższy przykład pokazuje, jak ustawić <xref:System.Windows.ResourceDictionary>.</span><span class="sxs-lookup"><span data-stu-id="cea70-112">The following example shows how to set the <xref:System.Windows.ResourceDictionary>.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 <span data-ttu-id="cea70-113">Poniżej pokazano, jak można uzyskać zasobów zakresu aplikacji ze słownika zasobów udostępnianych przez <xref:System.Windows.Application.Resources%2A> w XAML.</span><span class="sxs-lookup"><span data-stu-id="cea70-113">The following shows how you can get application-scope resources from the resource dictionary exposed by <xref:System.Windows.Application.Resources%2A> in XAML.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#4](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 <span data-ttu-id="cea70-114">Poniżej przedstawiono, jak również zawiera zasoby w kodzie.</span><span class="sxs-lookup"><span data-stu-id="cea70-114">The following shows how you can also get the resources in code.</span></span>  
  
 [!code-csharp[HOWTOResourceDictionaries#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 <span data-ttu-id="cea70-115">Istnieją dwie kwestie podczas korzystania z <xref:System.Windows.Application.Resources%2A>.</span><span class="sxs-lookup"><span data-stu-id="cea70-115">There are two considerations to make when using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="cea70-116">Po pierwsze, słownika *klucza* jest obiektem, więc należy użyć dokładnie tego samego wystąpienia obiektu podczas ustawiania i pobierania wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="cea70-116">First, the dictionary *key* is an object, so you must use exactly the same object instance when both setting and getting a property value.</span></span> <span data-ttu-id="cea70-117">(Zwróć uwagę, że klucz jest rozróżniana wielkość liter, przy użyciu ciągu). Drugi, słownika *wartość* jest obiektem, dlatego trzeba przekonwertować wartości na żądany typ podczas pobierania wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="cea70-117">(Note that the key is case-sensitive when using a string.) Second, the dictionary *value* is an object, so you will have to convert the value to the desired type when getting a property value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cea70-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cea70-118">See also</span></span>
- <xref:System.Windows.ResourceDictionary>
- <xref:System.Windows.Application.Resources%2A>
- [<span data-ttu-id="cea70-119">Zasoby XAML</span><span class="sxs-lookup"><span data-stu-id="cea70-119">XAML Resources</span></span>](../advanced/xaml-resources.md)
- [<span data-ttu-id="cea70-120">Połączone słowniki zasobów</span><span class="sxs-lookup"><span data-stu-id="cea70-120">Merged Resource Dictionaries</span></span>](../advanced/merged-resource-dictionaries.md)
