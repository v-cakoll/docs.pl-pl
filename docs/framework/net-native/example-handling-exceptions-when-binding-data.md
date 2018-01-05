---
title: "Przykład: obsługa wyjątków podczas powiązywania danych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd63ed96-9853-46dc-ade5-7bd1b0f39110
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e2714d53426bfee22b3d83d76b766816d9bc9d60
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="example-handling-exceptions-when-binding-data"></a>Przykład: obsługa wyjątków podczas powiązywania danych
> [!NOTE]
>  W tym temacie odnosi się do .NET Native Developer Preview, która jest wersja wstępna oprogramowania. Możesz pobrać podglądu [witryny sieci Web Microsoft Connect](http://go.microsoft.com/fwlink/?LinkId=394611) (wymaga rejestracji).  
  
 Poniższy przykład przedstawia sposób rozwiązania [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) wyjątek zgłaszany, gdy aplikacja jest skompilowana przy użyciu [!INCLUDE[net_native](../../../includes/net-native-md.md)] łańcucha narzędzi próbuje powiązać dane. Poniżej przedstawiono informacje o wyjątku:  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:   
App.ViewModels.MainPageVM  
```  
  
 Stos wywołań skojarzony jest następujący:  
  
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
  
## <a name="what-was-the-app-doing"></a>Co wykonywanych aplikacji?  
 U podstawy stosu ramki z [Windows.UI.Xaml](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.aspx) przestrzeni nazw wskazują, że aparat renderowania XAML został uruchomiony.   Korzystanie z <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> metoda wskazuje oparty na odbiciu wyszukiwania wartości właściwości w typie, którego metadanych został usunięty.  
  
 Pierwszym krokiem w zapewnianiu dyrektywy metadanych byłoby dodać `serialize` metadanych dla typu tak, aby jego właściwości są wszystkie dostępne:  
  
```xml  
<Type Name="App.ViewModels.MainPageVM" Serialize="Required Public" />  
```  
  
## <a name="is-this-an-isolated-case"></a>To jest izolowane przypadku?  
 W tym scenariuszu, jeśli wiązanie danych ma niekompletne metadane dla jednego `ViewModel`, może ona dla innych osób, zbyt.  Jeśli kod jest strukturę w aplikacji wyświetlanie modeli są w sposób `App.ViewModels` przestrzeni nazw, można użyć ogólniejszych dyrektyw środowiska uruchomieniowego:  
  
```xml  
<Namespace Name="App.ViewModels " Serialize="Required Public" />  
```  
  
## <a name="could-the-code-be-rewritten-to-not-use-reflection"></a>Można kod ponownego napisania nieużywanie odbicia?  
 Powiązanie danych jest intensywnie odbicia, zmiana kodu w celu uniknięcia odbicia nie jest możliwe.  
  
 Istnieją jednak sposoby określania `ViewModel` do strony XAML, dzięki czemu można skojarzyć łańcucha narzędzi właściwości powiązania poprawnego typu na czas kompilacji i Zachowaj metadane bez użycia dyrektyw środowiska uruchomieniowego.  Na przykład można zastosować [Windows.UI.Xaml.Data.BindableAttribute](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.data.bindableattribute.aspx) atrybutu dla właściwości. To spowoduje, że kompilatora XAML wygenerować informacje wymagane wyszukiwania i pozwala uniknąć konieczności dyrektywy środowiska uruchomieniowego w pliku Default.rd.xml.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [Przykład: Rozwiązywanie problemów z programowaniem dynamicznym](../../../docs/framework/net-native/example-troubleshooting-dynamic-programming.md)
