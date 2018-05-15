---
title: 'Przykład: obsługa wyjątków podczas powiązywania danych'
ms.date: 03/30/2017
ms.assetid: bd63ed96-9853-46dc-ade5-7bd1b0f39110
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c4b73ed36d3334e983b960ce972292a190bad85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="example-handling-exceptions-when-binding-data"></a><span data-ttu-id="62fbe-102">Przykład: obsługa wyjątków podczas powiązywania danych</span><span class="sxs-lookup"><span data-stu-id="62fbe-102">Example: Handling Exceptions When Binding Data</span></span>
> [!NOTE]
>  <span data-ttu-id="62fbe-103">W tym temacie odnosi się do .NET Native Developer Preview, która jest wersja wstępna oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="62fbe-103">This topic refers to the .NET Native Developer Preview, which is pre-release software.</span></span> <span data-ttu-id="62fbe-104">Możesz pobrać podglądu [witryny sieci Web Microsoft Connect](http://go.microsoft.com/fwlink/?LinkId=394611) (wymaga rejestracji).</span><span class="sxs-lookup"><span data-stu-id="62fbe-104">You can download the preview from the [Microsoft Connect website](http://go.microsoft.com/fwlink/?LinkId=394611) (requires registration).</span></span>  
  
 <span data-ttu-id="62fbe-105">Poniższy przykład przedstawia sposób rozwiązania [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) wyjątek zgłaszany, gdy aplikacja jest skompilowana przy użyciu [!INCLUDE[net_native](../../../includes/net-native-md.md)] łańcucha narzędzi próbuje powiązać dane.</span><span class="sxs-lookup"><span data-stu-id="62fbe-105">The following example shows how to resolve a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception that is thrown when an app compiled with the [!INCLUDE[net_native](../../../includes/net-native-md.md)] tool chain tries to bind data.</span></span> <span data-ttu-id="62fbe-106">Poniżej przedstawiono informacje o wyjątku:</span><span class="sxs-lookup"><span data-stu-id="62fbe-106">Here’s the exception information:</span></span>  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:   
App.ViewModels.MainPageVM  
```  
  
 <span data-ttu-id="62fbe-107">Stos wywołań skojarzony jest następujący:</span><span class="sxs-lookup"><span data-stu-id="62fbe-107">Here's the associated call stack:</span></span>  
  
```  
Reflection::Execution::ReflectionDomainSetupImplementation.CreateNonInvokabilityException+0x238  
Reflection::Core::ReflectionDomain.CreateNonInvokabilityException+0x2e  
Reflection::Core::Execution::ExecutionEnvironment.+0x316  
System::Reflection::Runtime::PropertyInfos::RuntimePropertyInfo.GetValue+0x1cb  
System::Reflection::PropertyInfo.GetValue+0x22  
System::Runtime::InteropServices::WindowsRuntime::CustomPropertyImpl.GetValue+0x42  
App!$66_Interop::McgNative.Func_IInspectable_IInspectable+0x158  
App!$66_Interop::McgNative::__vtable_Windows_UI_Xaml_Data__ICustomProperty.GetValue__STUB+0x46  
Windows_UI_Xaml!DirectUI::PropertyProviderPropertyAccess::GetValue+0x3f   
Windows_UI_Xaml!DirectUI::PropertyAccessPathStep::GetValue+0x31   
Windows_UI_Xaml!DirectUI::PropertyPathListener::ConnectPathStep+0x113  
```  
  
## <a name="what-was-the-app-doing"></a><span data-ttu-id="62fbe-108">Co wykonywanych aplikacji?</span><span class="sxs-lookup"><span data-stu-id="62fbe-108">What was the app doing?</span></span>  
 <span data-ttu-id="62fbe-109">U podstawy stosu ramki z [Windows.UI.Xaml](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.aspx) przestrzeni nazw wskazują, że aparat renderowania XAML został uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="62fbe-109">At the base of the stack, frames from the [Windows.UI.Xaml](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.aspx) namespace indicate that the XAML rendering engine was running.</span></span>   <span data-ttu-id="62fbe-110">Korzystanie z <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> metoda wskazuje oparty na odbiciu wyszukiwania wartości właściwości w typie, którego metadanych został usunięty.</span><span class="sxs-lookup"><span data-stu-id="62fbe-110">The use of the <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> method indicates a reflection-based lookup of a property’s value on the type whose metadata was removed.</span></span>  
  
 <span data-ttu-id="62fbe-111">Pierwszym krokiem w zapewnianiu dyrektywy metadanych byłoby dodać `serialize` metadanych dla typu tak, aby jego właściwości są wszystkie dostępne:</span><span class="sxs-lookup"><span data-stu-id="62fbe-111">The first step in providing a metadata directive would be to add `serialize` metadata for the type so that its properties are all accessible:</span></span>  
  
```xml  
<Type Name="App.ViewModels.MainPageVM" Serialize="Required Public" />  
```  
  
## <a name="is-this-an-isolated-case"></a><span data-ttu-id="62fbe-112">To jest izolowane przypadku?</span><span class="sxs-lookup"><span data-stu-id="62fbe-112">Is this an isolated case?</span></span>  
 <span data-ttu-id="62fbe-113">W tym scenariuszu, jeśli wiązanie danych ma niekompletne metadane dla jednego `ViewModel`, może ona dla innych osób, zbyt.</span><span class="sxs-lookup"><span data-stu-id="62fbe-113">In this scenario, if data binding has incomplete metadata for one `ViewModel`, it may for others, too.</span></span>  <span data-ttu-id="62fbe-114">Jeśli kod jest strukturę w aplikacji wyświetlanie modeli są w sposób `App.ViewModels` przestrzeni nazw, można użyć ogólniejszych dyrektyw środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="62fbe-114">If the code is structured in a way that the app’s view models are all in the `App.ViewModels` namespace, you could use a more general runtime directive:</span></span>  
  
```xml  
<Namespace Name="App.ViewModels " Serialize="Required Public" />  
```  
  
## <a name="could-the-code-be-rewritten-to-not-use-reflection"></a><span data-ttu-id="62fbe-115">Można kod ponownego napisania nieużywanie odbicia?</span><span class="sxs-lookup"><span data-stu-id="62fbe-115">Could the code be rewritten to not use reflection?</span></span>  
 <span data-ttu-id="62fbe-116">Powiązanie danych jest intensywnie odbicia, zmiana kodu w celu uniknięcia odbicia nie jest możliwe.</span><span class="sxs-lookup"><span data-stu-id="62fbe-116">Because data binding is reflection-intensive, changing the code to avoid reflection isn’t feasible.</span></span>  
  
 <span data-ttu-id="62fbe-117">Istnieją jednak sposoby określania `ViewModel` do strony XAML, dzięki czemu można skojarzyć łańcucha narzędzi właściwości powiązania poprawnego typu na czas kompilacji i Zachowaj metadane bez użycia dyrektyw środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="62fbe-117">However, there are ways to specify the `ViewModel` to the XAML page so that the tool chain can associate property bindings with the correct type at compile time and keep the metadata without using a runtime directive.</span></span>  <span data-ttu-id="62fbe-118">Na przykład można zastosować [Windows.UI.Xaml.Data.BindableAttribute](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.data.bindableattribute.aspx) atrybutu dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="62fbe-118">For example, you could apply the [Windows.UI.Xaml.Data.BindableAttribute](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.data.bindableattribute.aspx) attribute on properties.</span></span> <span data-ttu-id="62fbe-119">To spowoduje, że kompilatora XAML wygenerować informacje wymagane wyszukiwania i pozwala uniknąć konieczności dyrektywy środowiska uruchomieniowego w pliku Default.rd.xml.</span><span class="sxs-lookup"><span data-stu-id="62fbe-119">This causes the XAML compiler to generate the required lookup information and avoids requiring a runtime directive in the Default.rd.xml file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62fbe-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="62fbe-120">See Also</span></span>  
 [<span data-ttu-id="62fbe-121">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="62fbe-121">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [<span data-ttu-id="62fbe-122">Przykład: Rozwiązywanie problemów z programowaniem dynamicznym</span><span class="sxs-lookup"><span data-stu-id="62fbe-122">Example: Troubleshooting Dynamic Programming</span></span>](../../../docs/framework/net-native/example-troubleshooting-dynamic-programming.md)
