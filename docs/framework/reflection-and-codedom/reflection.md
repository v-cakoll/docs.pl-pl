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
ms.openlocfilehash: ab4a31195a202929c8485349cbf43235faea8e2d
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221241"
---
# <a name="reflection-in-the-net-framework"></a>Odbicie w oprogramowaniu .NET Framework
Klasy w <xref:System.Reflection> przestrzeni nazw, wraz z <xref:System.Type?displayProperty=nameWithType>, umożliwiają uzyskanie informacji na temat załadować [zestawy](../app-domains/assemblies-in-the-common-language-runtime.md) i typy zdefiniowane w nich, takich jak [klasy](../../standard/base-types/common-type-system.md#classes), [interfejsów](../../standard/base-types/common-type-system.md#interfaces), i [typy wartości](../../csharp/language-reference/keywords/value-types.md). Można również używać odbicia do tworzenia wystąpień typów w czasie wykonywania, a także wywołania i uzyskiwać do nich dostęp. Tematy dotyczące konkretnych aspektów odbicia, zobacz [Tematy pokrewne](#related_topics) na końcu tego omówienia.
  
 [Środowiska uruchomieniowego języka wspólnego](../../../docs/standard/clr.md) zarządza modułu ładującego [domen aplikacji](../../../docs/framework/app-domains/application-domains.md), które stanowią zdefiniowane granice wokół obiektów, które mają ten sam zakres aplikacji. Zarządzania obejmuje ładowania każdego zestawu do odpowiedniej domeny aplikacji i kontrolowanie układu pamięci hierarchii typów w obrębie każdego zestawu.  
  
 [Zestawy](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md) zawierać moduły, moduły zawierają typy, a typy elementów członkowskich. Odbicie zawiera obiekty, które hermetyzują zestawy, moduły i typy. Za pomocą odbicia do dynamicznego utworzenia wystąpienia typu, powiązania typu z istniejącego obiektu lub uzyskania typu z istniejącego obiektu. Następnie można wywołać metody typu lub dostęp do jego pola i właściwości. Typowe zastosowania odbicia obejmują następujące czynności:  
  
-   Użyj <xref:System.Reflection.Assembly> do definiowania i ładować zestawy, ładowanie modułów, które są wymienione w manifeście zestawu, a następnie znajdź typu z tego zestawu i utworzyć wystąpienie.  
  
-   Użyj <xref:System.Reflection.Module> aby odkryć informacje, takie jak zestaw, który zawiera moduł i klasy w module. Można również uzyskać wszystkie metody globalne lub innych metod określone, nieglobalnych, zdefiniowane w module.  
  
-   Użyj <xref:System.Reflection.ConstructorInfo> Aby znaleźć informacje, takie jak nazwa, parametrów, modyfikatorach dostępu (takich jak `public` lub `private`) i szczegółów implementacji (takie jak `abstract` lub `virtual`) konstruktora. Użyj <xref:System.Type.GetConstructors%2A> lub <xref:System.Type.GetConstructor%2A> metody <xref:System.Type> do wywołania określonego konstruktora.  
  
-   Użyj <xref:System.Reflection.MethodInfo> Aby znaleźć informacje, takie jak nazwa, zwracany typ i parametry, modyfikatory dostępu (takich jak `public` lub `private`) i szczegółów implementacji (takie jak `abstract` lub `virtual`) metody. Użyj <xref:System.Type.GetMethods%2A> lub <xref:System.Type.GetMethod%2A> metody <xref:System.Type> do wywołania określonej metody.  
  
-   Użyj <xref:System.Reflection.FieldInfo> Aby znaleźć informacje, takie jak nazwa, modyfikatorach dostępu (takich jak `public` lub `private`) i szczegółów implementacji (takie jak `static`) pola, a także pobierania lub ustawiania wartości pól.  
  
-   Użyj <xref:System.Reflection.EventInfo> odkryć informacje, takie jak nazwa, typ danych program obsługi zdarzeń, atrybutów niestandardowych, deklarowanie typów i odbitych typu zdarzenia, a także dodawanie lub usuwanie programów obsługi zdarzeń.  
  
-   Użyj <xref:System.Reflection.PropertyInfo> Aby znaleźć informacje, takie jak nazwa, typ danych, deklarowania typu, odzwierciedlone typu i tylko do odczytu lub zapisu stanu właściwości, a także pobierania lub ustawiania wartości właściwości.  
  
-   Użyj <xref:System.Reflection.ParameterInfo> aby odkryć informacje, takie jak nazwa parametru, typ danych, czy parametr wejściowy lub parametru wyjściowego i pozycja parametru w podpisie metody.  
  
-   Użyj <xref:System.Reflection.CustomAttributeData> do wykrywania informacji na temat atrybutów niestandardowych, gdy pracujesz w kontekstu reflection-only domeny aplikacji. <xref:System.Reflection.CustomAttributeData> można zbadać atrybutów bez tworzenia wystąpienia.  
  
 Klasy <xref:System.Reflection.Emit> przestrzeń nazw zapewnia formą specjalistyczne odbicia, która umożliwia tworzenie typów w czasie wykonywania.  
  
 Odbicie może służyć także do tworzenia aplikacji o nazwie typu przeglądarek, które umożliwiają użytkownikom wybór typów, a następnie wyświetlić informacje o tych typach.  
  
 Istnieją inne sposoby odbicia. Kompilatory języków, takich jak JScript używać odbicia do konstruowania tabele symboli. Klasy w <xref:System.Runtime.Serialization> przestrzeni nazw używać odbicia, aby uzyskiwać dostęp do danych oraz określić pola, które można utrwalić. Klasy w <xref:System.Runtime.Remoting> przestrzeni nazw używać odbicia pośrednio za pomocą serializacji.  
  
## <a name="runtime-types-in-reflection"></a>Typy środowiska uruchomieniowego w odbiciu  
 Odbicie udostępnia klasy, takie jak <xref:System.Type> i <xref:System.Reflection.MethodInfo>, do reprezentowania typów, elementów członkowskich, parametry i inne jednostki kodu. Gdy używasz odbicia nie działają bezpośrednio z tych klas, z których większość są jednak abstrakcyjny (`MustInherit` w języku Visual Basic). Zamiast tego możesz pracować z typów dostarczonych przez środowisko uruchomieniowe języka wspólnego (CLR).  
  
 Na przykład, kiedy używasz języka C# `typeof` — operator (`GetType` w języku Visual Basic) do uzyskania <xref:System.Type> obiektu, obiekt jest rzeczywiście `RuntimeType`. `RuntimeType` pochodzi od klasy <xref:System.Type>i zawiera implementacje wszystkie metody abstrakcyjne.  
  
 Te klasy środowiska uruchomieniowego są `internal` (`Friend` w języku Visual Basic). Mogą nie opisano oddzielnie z ich klasami podstawowymi, ponieważ ich zachowanie jest opisany w dokumentacji klasy bazowej.  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Wyświetlanie informacji o typie](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)|W tym artykule opisano <xref:System.Type> klasy i przykłady kodu, które ilustrują sposób korzystania <xref:System.Type> z kilku klas odbicia w celu uzyskania informacji na temat konstruktorów, metody, pola, właściwości i zdarzenia.|  
|[Odbicie i typy ogólne](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)|W tym artykule wyjaśniono, jak odbicie obsługuje parametrów typu i argumentów typu rodzajowego typów i metod ogólnych.|  
|[Zagadnienia dotyczące zabezpieczeń dla odbicia](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md)|W tym artykule opisano zasady określające, w jakim stopniu odbicie może służyć do odnajdywanie typu informacji i dostęp do typów.|  
|[Dynamiczne ładowanie i używanie typów](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md)|W tym artykule opisano interfejs niestandardowego powiązania odbicia, który obsługuje późnego wiązania.|  
|[Instrukcje: Ładowanie zestawów do kontekstu Reflection-Only](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)|W tym artykule opisano kontekstu ładowania tylko odbicie. Pokazuje sposób załadowania zestawu, jak przetestować kontekst oraz zbadania atrybuty stosowane do zestawu w kontekstu reflection-only.|  
|[Uzyskiwanie dostępu do atrybutów niestandardowych](../../../docs/framework/reflection-and-codedom/accessing-custom-attributes.md)|Demonstruje użycie odbicia do istnienia atrybut zapytania i wartości.|  
|[Określanie w pełni kwalifikowanych nazw typów](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)|Opisuje format w pełni kwalifikowanych nazw typów w postaci notacji Backusa-Naura (BNF) oraz składni wymaganej do określania znaków specjalnych, nazwy zestawu, wskaźników, odwołań i tablic.|  
|[Instrukcje: Podłączanie delegata za pomocą odbicia](../../../docs/framework/reflection-and-codedom/how-to-hook-up-a-delegate-using-reflection.md)|Wyjaśnia, jak utworzyć delegata dla metody i podłączyć delegata do zdarzenia. Opis sposobu tworzenia metody obsługi zdarzeń w czasie wykonywania za pomocą <xref:System.Reflection.Emit.DynamicMethod>.|  
|[Emitowanie dynamicznych metod i zestawów](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)|Wyjaśnia, jak można wygenerować zestawów dynamicznych i metod dynamicznych.|  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Type?displayProperty=nameWithType>  
  
 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  
  
