---
title: 'Przykład: obsługa wyjątków podczas wiązania danych'
ms.date: 03/30/2017
ms.assetid: bd63ed96-9853-46dc-ade5-7bd1b0f39110
ms.openlocfilehash: b774d1bce4f4d1c03258ed44b27d3871e7c5275f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181023"
---
# <a name="example-handling-exceptions-when-binding-data"></a>Przykład: obsługa wyjątków podczas wiązania danych
> [!NOTE]
> Ten temat odnosi się do programu .NET Native Developer Preview, który jest oprogramowaniem w wersji wstępnej. Wersję zapoznawczą można pobrać ze [strony internetowej Microsoft Connect](https://go.microsoft.com/fwlink/?LinkId=394611) (wymaga rejestracji).  
  
 W poniższym przykładzie pokazano, jak rozwiązać [MissingMetadataException](missingmetadataexception-class-net-native.md) wyjątek, który jest generowany, gdy aplikacja skompilowana z .NET natywnego łańcucha narzędzi próbuje powiązać dane. Oto informacje o wyjątku:  
  
```output
This operation cannot be carried out as metadata for the following type was removed for performance reasons:
App.ViewModels.MainPageVM  
```  
  
 Oto skojarzony stos połączeń:  
  
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
  
## <a name="what-was-the-app-doing"></a>Co robiła aplikacja?  
 U podstawy stosu ramki z <xref:Windows.UI.Xaml?displayProperty=nameWithType> obszaru nazw wskazują, że aparat renderowania XAML był uruchomiony.   Użycie <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> metody wskazuje odbicie oparte na odbiciu wartości właściwości na typ, którego metadane zostały usunięte.  
  
 Pierwszym krokiem w dostarczaniu dyrektywy metadanych byłoby dodanie `serialize` metadanych dla typu, tak aby jego właściwości były dostępne:  
  
```xml  
<Type Name="App.ViewModels.MainPageVM" Serialize="Required Public" />  
```  
  
## <a name="is-this-an-isolated-case"></a>Czy jest to odosobniony przypadek?  
 W tym scenariuszu, jeśli powiązanie `ViewModel`danych ma niekompletne metadane dla jednego , może również dla innych.  Jeśli kod jest skonstruowany w taki sposób, że modele `App.ViewModels` widoku aplikacji znajdują się w obszarze nazw, można użyć bardziej ogólnej dyrektywy środowiska uruchomieniowego:  
  
```xml  
<Namespace Name="App.ViewModels " Serialize="Required Public" />  
```  
  
## <a name="could-the-code-be-rewritten-to-not-use-reflection"></a>Czy kod można przepisać, aby nie używać odbicia?  
 Ponieważ powiązanie danych jest intensywnie odbicie, zmiana kodu, aby uniknąć odbicia nie jest możliwe.  
  
 Istnieją jednak sposoby, `ViewModel` aby określić do strony XAML, tak aby łańcuch narzędzi można skojarzyć powiązania właściwości z poprawnym typem w czasie kompilacji i zachować metadane bez użycia dyrektywy środowiska uruchomieniowego.  Na przykład można zastosować <xref:Windows.UI.Xaml.Data.BindableAttribute?displayProperty=nameWithType> atrybut do właściwości. Powoduje to, że kompilator XAML do generowania wymaganych informacji o odszukaniu i unika konieczności dyrektywy środowiska uruchomieniowego w pliku Default.rd.xml.  
  
## <a name="see-also"></a>Zobacz też

- [Wprowadzenie](getting-started-with-net-native.md)
- [Przykład: rozwiązywanie problemów z programowaniem dynamicznym](example-troubleshooting-dynamic-programming.md)
