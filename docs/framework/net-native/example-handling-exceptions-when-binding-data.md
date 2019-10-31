---
title: 'Przykład: obsługa wyjątków podczas wiązania danych'
ms.date: 03/30/2017
ms.assetid: bd63ed96-9853-46dc-ade5-7bd1b0f39110
ms.openlocfilehash: 7ab5477257bd6d32d901ad01518f7a75081d2a10
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128455"
---
# <a name="example-handling-exceptions-when-binding-data"></a><span data-ttu-id="42bf4-102">Przykład: obsługa wyjątków podczas wiązania danych</span><span class="sxs-lookup"><span data-stu-id="42bf4-102">Example: Handling Exceptions When Binding Data</span></span>
> [!NOTE]
> <span data-ttu-id="42bf4-103">Ten temat dotyczy wersji zapoznawczej programu .NET Native Developer, która jest oprogramowaniem w wersji wstępnej.</span><span class="sxs-lookup"><span data-stu-id="42bf4-103">This topic refers to the .NET Native Developer Preview, which is pre-release software.</span></span> <span data-ttu-id="42bf4-104">Wersję zapoznawczą można pobrać z [witryny sieci Web Microsoft Connect](https://go.microsoft.com/fwlink/?LinkId=394611) (wymaga rejestracji).</span><span class="sxs-lookup"><span data-stu-id="42bf4-104">You can download the preview from the [Microsoft Connect website](https://go.microsoft.com/fwlink/?LinkId=394611) (requires registration).</span></span>  
  
 <span data-ttu-id="42bf4-105">Poniższy przykład pokazuje, jak rozpoznać wyjątek [MissingMetadataException](missingmetadataexception-class-net-native.md) , który jest generowany, gdy aplikacja skompilowana za pomocą łańcucha narzędzi .NET Native próbuje powiązać dane.</span><span class="sxs-lookup"><span data-stu-id="42bf4-105">The following example shows how to resolve a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception that is thrown when an app compiled with the .NET Native tool chain tries to bind data.</span></span> <span data-ttu-id="42bf4-106">Oto informacje o wyjątku:</span><span class="sxs-lookup"><span data-stu-id="42bf4-106">Here’s the exception information:</span></span>  
  
```output
This operation cannot be carried out as metadata for the following type was removed for performance reasons:   
App.ViewModels.MainPageVM  
```  
  
 <span data-ttu-id="42bf4-107">Oto skojarzony stos wywołań:</span><span class="sxs-lookup"><span data-stu-id="42bf4-107">Here's the associated call stack:</span></span>  
  
```output
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
  
## <a name="what-was-the-app-doing"></a><span data-ttu-id="42bf4-108">Co to jest aplikacja?</span><span class="sxs-lookup"><span data-stu-id="42bf4-108">What was the app doing?</span></span>  
 <span data-ttu-id="42bf4-109">W podstawowym stosie ramki z przestrzeni nazw <xref:Windows.UI.Xaml?displayProperty=nameWithType> wskazują, że aparat renderowania XAML był uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="42bf4-109">At the base of the stack, frames from the <xref:Windows.UI.Xaml?displayProperty=nameWithType> namespace indicate that the XAML rendering engine was running.</span></span>   <span data-ttu-id="42bf4-110">Użycie metody <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> wskazuje wyszukiwanie na podstawie odbicia wartości właściwości w typie, którego metadane zostały usunięte.</span><span class="sxs-lookup"><span data-stu-id="42bf4-110">The use of the <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> method indicates a reflection-based lookup of a property’s value on the type whose metadata was removed.</span></span>  
  
 <span data-ttu-id="42bf4-111">Pierwszym krokiem w dostarczaniu dyrektywy metadanych byłoby dodanie `serialize` metadanych dla tego typu, aby jego właściwości były dostępne:</span><span class="sxs-lookup"><span data-stu-id="42bf4-111">The first step in providing a metadata directive would be to add `serialize` metadata for the type so that its properties are all accessible:</span></span>  
  
```xml  
<Type Name="App.ViewModels.MainPageVM" Serialize="Required Public" />  
```  
  
## <a name="is-this-an-isolated-case"></a><span data-ttu-id="42bf4-112">Czy to jest izolowany przypadek?</span><span class="sxs-lookup"><span data-stu-id="42bf4-112">Is this an isolated case?</span></span>  
 <span data-ttu-id="42bf4-113">W tym scenariuszu, Jeśli powiązanie danych zawiera niekompletne metadane dla jednego `ViewModel`, może być również dla innych.</span><span class="sxs-lookup"><span data-stu-id="42bf4-113">In this scenario, if data binding has incomplete metadata for one `ViewModel`, it may for others, too.</span></span>  <span data-ttu-id="42bf4-114">Jeśli kod jest strukturalny w sposób, w którym wszystkie modele widoku aplikacji znajdują się w przestrzeni nazw `App.ViewModels`, można użyć bardziej ogólnej dyrektywy środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="42bf4-114">If the code is structured in a way that the app’s view models are all in the `App.ViewModels` namespace, you could use a more general runtime directive:</span></span>  
  
```xml  
<Namespace Name="App.ViewModels " Serialize="Required Public" />  
```  
  
## <a name="could-the-code-be-rewritten-to-not-use-reflection"></a><span data-ttu-id="42bf4-115">Czy kod można napisać ponownie, aby nie używać odbicia?</span><span class="sxs-lookup"><span data-stu-id="42bf4-115">Could the code be rewritten to not use reflection?</span></span>  
 <span data-ttu-id="42bf4-116">Ponieważ powiązanie danych jest intensywnym odbiciem, zmiana kodu, aby uniknąć odbicia, nie jest możliwe.</span><span class="sxs-lookup"><span data-stu-id="42bf4-116">Because data binding is reflection-intensive, changing the code to avoid reflection isn’t feasible.</span></span>  
  
 <span data-ttu-id="42bf4-117">Istnieją jednak sposoby określania `ViewModel` na stronie XAML, dzięki czemu łańcuch narzędzi może kojarzyć powiązania właściwości z poprawnym typem w czasie kompilacji i zachować metadane bez użycia dyrektywy środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="42bf4-117">However, there are ways to specify the `ViewModel` to the XAML page so that the tool chain can associate property bindings with the correct type at compile time and keep the metadata without using a runtime directive.</span></span>  <span data-ttu-id="42bf4-118">Na przykład można zastosować atrybut <xref:Windows.UI.Xaml.Data.BindableAttribute?displayProperty=nameWithType> we właściwościach.</span><span class="sxs-lookup"><span data-stu-id="42bf4-118">For example, you could apply the <xref:Windows.UI.Xaml.Data.BindableAttribute?displayProperty=nameWithType> attribute on properties.</span></span> <span data-ttu-id="42bf4-119">Powoduje to wygenerowanie wymaganych informacji wyszukiwania przez kompilator XAML i uniknięcie wymagania dyrektywy środowiska uruchomieniowego w pliku default. Rd. XML.</span><span class="sxs-lookup"><span data-stu-id="42bf4-119">This causes the XAML compiler to generate the required lookup information and avoids requiring a runtime directive in the Default.rd.xml file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42bf4-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="42bf4-120">See also</span></span>

- [<span data-ttu-id="42bf4-121">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="42bf4-121">Getting Started</span></span>](getting-started-with-net-native.md)
- [<span data-ttu-id="42bf4-122">Przykład: Rozwiązywanie problemów z programowaniem dynamicznym</span><span class="sxs-lookup"><span data-stu-id="42bf4-122">Example: Troubleshooting Dynamic Programming</span></span>](example-troubleshooting-dynamic-programming.md)
