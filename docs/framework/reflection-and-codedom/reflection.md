---
title: Odbicie w oprogramowaniu .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], reflection
- EventInfo class, reflection
- common language runtime, reflection
- FieldInfo class, reflection
- ParameterInfo class, reflection
- ConstructorInfo class, reflection
- Assembly class, reflection
- value types, reflection
- reflection, about reflection
- modules, reflection
- runtime, reflection
- Module class, reflection
- MethodInfo class, reflection
- PropertyInfo class, reflection
- type browsers
- reflection
- discovering type information at run time
- type system, reflection
ms.assetid: d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ef4e2918b682d964b7f65eb98d497715d1e4ac57
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="reflection-in-the-net-framework"></a>Odbicie w oprogramowaniu .NET Framework
Klasy w <xref:System.Reflection> przestrzeni nazw, wraz z <xref:System.Type?displayProperty=nameWithType>, umożliwiają uzyskanie informacji na temat załadować [zestawy](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md) i typy zdefiniowane w nich, takich jak [klasy](http://msdn.microsoft.com/library/ad7d3561-271e-4546-82fc-e00b059f27a9), [interfejsów](http://msdn.microsoft.com/library/fd9d5975-5363-4bc9-b883-609f887895e5), i [typów wartości](http://msdn.microsoft.com/library/c9c567f8-8ab1-4d88-834d-00f7d92418de). Umożliwia także odbicia Tworzenie wystąpień typów w czasie wykonywania, a także wywołania i uzyskiwać do nich dostęp. Tematy dotyczące określonych aspektów odbicia, zobacz [Tematy pokrewne](#related_topics) na końcu tego przeglądu.  
  
 [Środowisko uruchomieniowe języka wspólnego](../../../docs/standard/clr.md) zarządza modułu ładującego [domen aplikacji](../../../docs/framework/app-domains/application-domains.md), które stanowią zdefiniowane granice wokół obiektów, które mają ten sam zakres aplikacji. To zarządzanie obejmuje ładowania każdego zestawu, do odpowiedniej domeny aplikacji i określania układu pamięci hierarchii typów w każdym zestawie.  
  
 [Zestawy](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md) zawierać modułów, moduły zawierają typów, a typy elementów członkowskich. Odbicie zawiera obiekty, które hermetyzują zestawy, moduły i typy. Odbicie umożliwia dynamicznie utworzyć wystąpienia typu, powiązanie typu obiektu lub pobranie typu z istniejącego obiektu. Można wywołać metody typu lub uzyskiwać dostęp do swoich pól i właściwości. Typowym zastosowaniem odbicia są następujące:  
  
-   Użyj <xref:System.Reflection.Assembly> do definiowania i ładowanie zestawów, ładowanie modułów, które są wymienione w manifeście zestawu i zlokalizować typu z tego zestawu i Utwórz wystąpienie.  
  
-   Użyj <xref:System.Reflection.Module> informacji takich jak zestaw zawierający moduł i klasy w module. Można także uzyskać wszystkie metody globalne lub innych metod określone, nieglobalnych zdefiniowane w module.  
  
-   Użyj <xref:System.Reflection.ConstructorInfo> odnaleźć informacje takie jak nazwa, parametry, dostępu do Modyfikatory (takich jak `public` lub `private`) i szczegóły implementacji (takich jak `abstract` lub `virtual`) konstruktora. Użyj <xref:System.Type.GetConstructors%2A> lub <xref:System.Type.GetConstructor%2A> metody <xref:System.Type> do wywołania określonych konstruktora.  
  
-   Użyj <xref:System.Reflection.MethodInfo> odnajdywania informacje, takie jak nazwa, zwracany typ i parametry, modyfikatory dostępu (takich jak `public` lub `private`) i szczegóły implementacji (takich jak `abstract` lub `virtual`) metody. Użyj <xref:System.Type.GetMethods%2A> lub <xref:System.Type.GetMethod%2A> metody <xref:System.Type> można wywołać określonej metody.  
  
-   Użyj <xref:System.Reflection.FieldInfo> odnaleźć informacje takie jak nazwa, dostępu do Modyfikatory (takich jak `public` lub `private`) i szczegóły implementacji (takie jak `static`) pola i do pobierania lub ustawiania wartości pól.  
  
-   Użyj <xref:System.Reflection.EventInfo> informacji takich jak nazwa, typ danych program obsługi zdarzeń, atrybutów niestandardowych, deklarowanie typów i odbite typu zdarzenia oraz do dodawania lub usuwania programów obsługi zdarzeń.  
  
-   Użyj <xref:System.Reflection.PropertyInfo> odnajdywania informacje, takie jak nazwa, typ danych, deklarowanie typu odzwierciedlone typu i tylko do odczytu lub zapisu stanu właściwości oraz do pobierania lub ustawiania wartości właściwości.  
  
-   Użyj <xref:System.Reflection.ParameterInfo> odnajdywania informacje, takie jak nazwa parametru, typ danych, czy parametr jest wartością wejściową lub parametru wyjściowego i pozycja parametru w podpisie metody.  
  
-   Użyj <xref:System.Reflection.CustomAttributeData> do wykrywania informacji na temat atrybutów niestandardowych, gdy użytkownik pracuje w kontekście "tylko odbicie" domeny aplikacji. <xref:System.Reflection.CustomAttributeData> można zbadać atrybutów bez tworzenia wystąpień z nich.  
  
 Klasy <xref:System.Reflection.Emit> przestrzeni nazw Podaj specjalna forma odbicia, która umożliwia tworzenie typów w czasie wykonywania.  
  
 Odbicie mogą służyć do tworzenia aplikacji o nazwie typu przeglądarek, które umożliwiają użytkownikom wybór typów, a następnie Wyświetl informacje o tych typach.  
  
 Istnieją inne sposoby odbicia. Kompilatory dla języków, takich jak JScript używać odbicia do tworzenia tabel symboli. Klasy w <xref:System.Runtime.Serialization> przestrzeni nazw użyj odbicia dostępu do danych i które pola do innej witryny. Klasy w <xref:System.Runtime.Remoting> przestrzeni nazw użyj odbicia pośrednio za pomocą serializacji.  
  
## <a name="runtime-types-in-reflection"></a>Typy środowiska uruchomieniowego w odbiciu  
 Odbicie udostępnia klasy, takich jak <xref:System.Type> i <xref:System.Reflection.MethodInfo>, do reprezentowania typów, elementy członkowskie, parametry oraz inne jednostki kodu. Jednak gdy używasz odbicia nie działają bezpośrednio z tych klas, z których większość są klasami abstrakcyjnymi (`MustInherit` w języku Visual Basic). Zamiast tego możesz pracować z typów dostarczanych przez środowisko uruchomieniowe języka wspólnego (CLR).  
  
 Na przykład, jeśli używasz języka C# `typeof` — operator (`GetType` w języku Visual Basic) można uzyskać <xref:System.Type> obiektu, obiekt jest w rzeczywistości `RuntimeType`. `RuntimeType` pochodną <xref:System.Type>i zawiera implementacje metody abstrakcyjne.  
  
 Te klasy środowiska uruchomieniowego są `internal` (`Friend` w języku Visual Basic). Ich nie opisano oddzielnie z ich klasami podstawowymi, ponieważ ich zachowanie jest opisane w dokumentacji klasy podstawowej.  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Wyświetlanie informacji o typie](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)|W tym artykule opisano <xref:System.Type> klasy i przykłady kodu, które ilustrują sposób użycia <xref:System.Type> z kilku klas odbicia, aby uzyskać informacje o konstruktorów, metod, pola, właściwości i zdarzeń.|  
|[Odbicie i typy ogólne](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)|W tym artykule wyjaśniono, jak odbicia obsługuje parametrów typu i argumentów typu ogólnego typów i metod ogólnych.|  
|[Zagadnienia dotyczące zabezpieczeń dla odbicia](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md)|W tym artykule opisano zasady, które określają, w jakim stopniu odbicia może służyć do wykrywania typu typy dostępu i informacji.|  
|[Dynamiczne ładowanie i używanie typów](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md)|Opisuje interfejs niestandardowe — wiązanie odbicia, który obsługuje późnego wiązania.|  
|[Instrukcje: ładowanie zestawów do kontekstu Reflection-Only](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)|W tym artykule opisano kontekstu ładowania tylko odbicie. Pokazuje, jak można załadować zestawu, jak przetestować kontekstu i jak zbadać atrybutów zastosowany do zestawu w kontekstu reflection-only.|  
|[Uzyskiwanie dostępu do atrybutów niestandardowych](../../../docs/framework/reflection-and-codedom/accessing-custom-attributes.md)|Pokazuje, za pomocą odbicia do istnienia atrybutu zapytania i wartości.|  
|[Określanie w pełni kwalifikowanych nazw typów](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)|W tym artykule opisano format w pełni kwalifikowane nazwy typów pod względem formularz Backus-naur (BNF) oraz składni wymaganej do określenia znaków specjalnych, nazwy zestawu wskaźników, odwołania i tablice.|  
|[Instrukcje: podłączanie delegata za pomocą odbicia](../../../docs/framework/reflection-and-codedom/how-to-hook-up-a-delegate-using-reflection.md)|Wyjaśniono, jak utworzyć delegata metody i utworzenie punktu zaczepienia delegata do zdarzenia. Wyjaśnia sposób tworzenia metody obsługi zdarzeń w czasie wykonywania za pomocą <xref:System.Reflection.Emit.DynamicMethod>.|  
|[Emitowanie dynamicznych metod i zestawów](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)|Wyjaśniono, jak generowanie zestawów dynamicznych i metod dynamicznych.|  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Type?displayProperty=nameWithType>  
  
 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  
  
