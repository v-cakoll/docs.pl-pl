---
title: 'Przykład: obsługa wyjątków podczas powiązywania danych'
ms.date: 03/30/2017
ms.assetid: bd63ed96-9853-46dc-ade5-7bd1b0f39110
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a861da011898c3648c66b6a0ea0f97cdb26ff288
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452763"
---
# <a name="example-handling-exceptions-when-binding-data"></a>Przykład: obsługa wyjątków podczas powiązywania danych
> [!NOTE]
>  W tym temacie odnosi się do platformy .NET Native Developer Preview, czyli wstępnej wersji oprogramowania. Możesz pobrać podglądu [witryny sieci Web Microsoft Connect](https://go.microsoft.com/fwlink/?LinkId=394611) (wymaga rejestracji).  
  
 Poniższy przykład pokazuje, jak rozwiązać [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) wyjątek, który jest zgłaszany, gdy aplikacja skompilowana przy użyciu [!INCLUDE[net_native](../../../includes/net-native-md.md)] łańcucha narzędzi próbuje powiązanie danych. Poniżej przedstawiono informacje o wyjątku:  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:   
App.ViewModels.MainPageVM  
```  
  
 Oto skojarzone stosu:  
  
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
  
## <a name="what-was-the-app-doing"></a>Została aplikacja działania?  
 Podstawową stosu, ramek z <xref:Windows.UI.Xaml?displayProperty=nameWithType> przestrzeni nazw wskazują, że aparat renderowania XAML została uruchomiona.   Korzystanie z <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> metoda wskazuje oparty na odbiciu wyszukiwania wartości właściwości w typie, którego metadanych został usunięty.  
  
 Pierwszym krokiem w dostarczaniu dyrektywy metadanych byłoby dodać `serialize` metadanych dla typu, aby jego właściwości są wszystkie dostępne:  
  
```xml  
<Type Name="App.ViewModels.MainPageVM" Serialize="Required Public" />  
```  
  
## <a name="is-this-an-isolated-case"></a>Jest to przypadek w izolowanym?  
 W tym scenariuszu, jeśli wiązanie danych ma niekompletne metadane dla jednego `ViewModel`, może ono innym, zbyt.  Jeśli kod jest umieszczonymi w taki sposób, że modeli widoków aplikacji są w `App.ViewModels` przestrzeni nazw, można użyć bardziej ogólnych dyrektyw środowiska uruchomieniowego:  
  
```xml  
<Namespace Name="App.ViewModels " Serialize="Required Public" />  
```  
  
## <a name="could-the-code-be-rewritten-to-not-use-reflection"></a>Można dopasować kod nie używać odbicia?  
 Wiązanie danych jest intensywnie korzystających z odbicia, zmiany kodu, aby uniknąć odbicie nie jest możliwe.  
  
 Istnieją sposoby określania `ViewModel` do strony XAML, dzięki czemu można skojarzyć łańcucha narzędzi właściwości powiązania przy użyciu poprawnego typu w czas kompilacji i zachować metadane bez przy użyciu dyrektyw środowiska uruchomieniowego.  Na przykład, można zastosować <xref:Windows.UI.Xaml.Data.BindableAttribute?displayProperty=nameWithType> atrybutu dla właściwości. To powoduje, że kompilator XAML do generowania informacji wymaganych wyszukiwania i pozwala uniknąć konieczności dyrektyw środowiska uruchomieniowego, w pliku Default.rd.xml.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [Przykład: Rozwiązywanie problemów z programowaniem dynamicznym](../../../docs/framework/net-native/example-troubleshooting-dynamic-programming.md)
