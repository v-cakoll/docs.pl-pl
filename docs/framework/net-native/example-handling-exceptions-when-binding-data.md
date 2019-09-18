---
title: 'Przykład: Obsługa wyjątków podczas wiązania danych'
ms.date: 03/30/2017
ms.assetid: bd63ed96-9853-46dc-ade5-7bd1b0f39110
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f7c40d1a179c29c3b92ca37848db6d1383e5d2d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049891"
---
# <a name="example-handling-exceptions-when-binding-data"></a>Przykład: Obsługa wyjątków podczas wiązania danych
> [!NOTE]
> Ten temat dotyczy wersji zapoznawczej programu .NET Native Developer, która jest oprogramowaniem w wersji wstępnej. Wersję zapoznawczą można pobrać z [witryny sieci Web Microsoft Connect](https://go.microsoft.com/fwlink/?LinkId=394611) (wymaga rejestracji).  
  
 Poniższy przykład pokazuje, jak rozpoznać wyjątek [MissingMetadataException](missingmetadataexception-class-net-native.md) , który jest generowany, gdy aplikacja skompilowana za pomocą łańcucha narzędzi .NET Native próbuje powiązać dane. Oto informacje o wyjątku:  
  
```output
This operation cannot be carried out as metadata for the following type was removed for performance reasons:   
App.ViewModels.MainPageVM  
```  
  
 Oto skojarzony stos wywołań:  
  
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
  
## <a name="what-was-the-app-doing"></a>Co to jest aplikacja?  
 W podstawowym stosie ramki z <xref:Windows.UI.Xaml?displayProperty=nameWithType> przestrzeni nazw wskazują, że aparat renderowania XAML był uruchomiony.   Użycie <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> metody wskazuje na podstawie odbicia wartość właściwości w typie, którego metadane zostały usunięte.  
  
 Pierwszym krokiem w dostarczaniu dyrektywy metadanych byłoby dodanie `serialize` metadanych dla tego typu, aby jego właściwości były dostępne:  
  
```xml  
<Type Name="App.ViewModels.MainPageVM" Serialize="Required Public" />  
```  
  
## <a name="is-this-an-isolated-case"></a>Czy to jest izolowany przypadek?  
 W tym scenariuszu, Jeśli powiązanie danych ma niekompletne metadane `ViewModel`dla jednej z nich, może być również dla innych.  Jeśli kod jest strukturalny w sposób, w którym wszystkie modele widoku aplikacji znajdują się w `App.ViewModels` przestrzeni nazw, można użyć bardziej ogólnej dyrektywy środowiska uruchomieniowego:  
  
```xml  
<Namespace Name="App.ViewModels " Serialize="Required Public" />  
```  
  
## <a name="could-the-code-be-rewritten-to-not-use-reflection"></a>Czy kod można napisać ponownie, aby nie używać odbicia?  
 Ponieważ powiązanie danych jest intensywnym odbiciem, zmiana kodu, aby uniknąć odbicia, nie jest możliwe.  
  
 Istnieją jednak sposoby określania `ViewModel` na stronie XAML, dzięki czemu łańcuch narzędzi może kojarzyć powiązania właściwości z poprawnym typem w czasie kompilacji i zachować metadane bez użycia dyrektywy środowiska uruchomieniowego.  Na przykład można zastosować <xref:Windows.UI.Xaml.Data.BindableAttribute?displayProperty=nameWithType> atrybut we właściwościach. Powoduje to wygenerowanie wymaganych informacji wyszukiwania przez kompilator XAML i uniknięcie wymagania dyrektywy środowiska uruchomieniowego w pliku default. Rd. XML.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie](getting-started-with-net-native.md)
- [Przykład: Rozwiązywanie problemów z programowaniem dynamicznym](example-troubleshooting-dynamic-programming.md)
