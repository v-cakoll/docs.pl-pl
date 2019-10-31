---
title: Odbicie w programie .NET
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET], reflection
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
ms.openlocfilehash: 1768acd65b738af068cf98a8b8340c3179e9b885
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130054"
---
# <a name="reflection-in-net"></a>Odbicie w programie .NET

Klasy w przestrzeni nazw <xref:System.Reflection>, w połączeniu z <xref:System.Type?displayProperty=nameWithType>, umożliwiają uzyskanie informacji o załadowanych [zestawach](../../standard/assembly/index.md) i typach zdefiniowanych w nich, takich jak [klasy](../../standard/base-types/common-type-system.md#classes), [interfejsy](../../standard/base-types/common-type-system.md#interfaces)i [typy wartości](../../csharp/language-reference/keywords/value-types.md). Można również użyć odbicia do tworzenia wystąpień typów w czasie wykonywania oraz do wywoływania i uzyskiwania dostępu do nich. Aby zapoznać się z tematami dotyczącymi konkretnych aspektów odbicia, zobacz [Tematy pokrewne](#related_topics) na końcu tego omówienia.
  
Moduł ładujący [środowiska uruchomieniowego języka wspólnego](../../standard/clr.md) zarządza [domenami aplikacji](../app-domains/application-domains.md), które stanowią zdefiniowane granice wokół obiektów, które mają ten sam zakres aplikacji. Zarządzanie obejmuje ładowanie każdego zestawu do odpowiedniej domeny aplikacji i sterowanie układem pamięci hierarchii typów w ramach każdego zestawu.  
  
[Zestawy](../app-domains/index.md) zawierają moduły, moduły zawierają typy, a typy zawierają elementy członkowskie. Odbicie zawiera obiekty, które hermetyzują zestawy, moduły i typy. Możesz użyć odbicia, aby dynamicznie utworzyć wystąpienie typu, powiązać typ z istniejącym obiektem lub uzyskać typ z istniejącego obiektu. Następnie można wywołać metody typu lub uzyskać dostęp do jego pól i właściwości. Typowe zastosowania odbicia obejmują następujące elementy:  
  
- Użyj <xref:System.Reflection.Assembly>, aby definiować i ładować zestawy, ładować moduły, które są wymienione w manifeście zestawu, i zlokalizować typ z tego zestawu i utworzyć wystąpienie.  
  
- Użyj <xref:System.Reflection.Module>, aby odnaleźć informacje takie jak zestaw, który zawiera moduł i klasy w module. Można również uzyskać wszystkie metody globalne lub inne określone, nieglobalne metody zdefiniowane w module.  
  
- Użyj <xref:System.Reflection.ConstructorInfo>, aby odnaleźć informacje takie jak nazwa, parametry, Modyfikatory dostępu (takie jak `public` lub `private`) i szczegóły implementacji (takie jak `abstract` lub `virtual`) konstruktora. Użyj metody <xref:System.Type.GetConstructors%2A> lub <xref:System.Type.GetConstructor%2A> <xref:System.Type>, aby wywołać określony Konstruktor.  
  
- Użyj <xref:System.Reflection.MethodInfo>, aby odnaleźć informacje takie jak nazwa, zwracany typ, parametry, Modyfikatory dostępu (takie jak `public` lub `private`) i szczegóły implementacji (takie jak `abstract` lub `virtual`) metody. Użyj metody <xref:System.Type.GetMethods%2A> lub <xref:System.Type.GetMethod%2A> <xref:System.Type>, aby wywołać określoną metodę.  
  
- Użyj <xref:System.Reflection.FieldInfo>, aby odnaleźć informacje takie jak nazwa, Modyfikatory dostępu (takie jak `public` lub `private`) i szczegóły implementacji (takie jak `static`) pola, i pobrać lub ustawić wartości pól.  
  
- Użyj <xref:System.Reflection.EventInfo>, aby odnaleźć informacje takie jak nazwa, typ danych programu obsługi zdarzeń, atrybuty niestandardowe, typ deklarujący i typ odbicia zdarzenia oraz dodać lub usunąć programy obsługi zdarzeń.  
  
- Użyj <xref:System.Reflection.PropertyInfo>, aby odnaleźć informacje takie jak nazwa, typ danych, typ deklarujący, typ odbicia i stan tylko do odczytu lub do zapisu właściwości, a także pobrać lub ustawić wartości właściwości.  
  
- Użyj <xref:System.Reflection.ParameterInfo>, aby odnaleźć informacje takie jak nazwa parametru, typ danych, czy parametr jest parametrem wejściowym lub wyjściowym, oraz pozycją parametru w podpisie metody.  
  
- Użyj <xref:System.Reflection.CustomAttributeData>, aby odnaleźć informacje o atrybutach niestandardowych podczas pracy w kontekście tylko odbicia w domenie aplikacji. <xref:System.Reflection.CustomAttributeData> umożliwia badanie atrybutów bez tworzenia wystąpień.  
  
Klasy przestrzeni nazw <xref:System.Reflection.Emit> zapewniają wyspecjalizowaną postać odbicia, która umożliwia kompilowanie typów w czasie wykonywania.  
  
Odbicie może również służyć do tworzenia aplikacji nazywanych przeglądarkami typu, które umożliwiają użytkownikom wybieranie typów, a następnie wyświetlanie informacji o tych typach.  
  
Istnieją inne zastosowania do odbicia. Kompilatory dla języków takich jak JScript używają odbicia do konstruowania tabel symboli. Klasy w przestrzeni nazw <xref:System.Runtime.Serialization> używają odbicia, aby uzyskiwać dostęp do danych i określać, które pola mają być utrwalane. Klasy w przestrzeni nazw <xref:System.Runtime.Remoting> używają odbicia pośrednio przy użyciu serializacji.  
  
## <a name="runtime-types-in-reflection"></a>Typy środowiska uruchomieniowego w odbiciu  
Odbicie zawiera klasy, takie jak <xref:System.Type> i <xref:System.Reflection.MethodInfo>, do reprezentowania typów, elementów członkowskich, parametrów i innych jednostek kodu. Jednak w przypadku używania odbicia nie można bezpośrednio korzystać z tych klas, z których większość jest abstrakcyjna (`MustInherit` w Visual Basic). Zamiast tego pracujesz z typami dostarczanymi przez środowisko uruchomieniowe języka wspólnego (CLR).  
  
Na przykład, gdy używasz operatora C# `typeof` (`GetType` w Visual Basic) do uzyskania obiektu <xref:System.Type>, obiekt jest w rzeczywistości `RuntimeType`. `RuntimeType` pochodzi od <xref:System.Type> i udostępnia implementacje wszystkich metod abstrakcyjnych.  
  
Te klasy środowiska uruchomieniowego są `internal` (`Friend` w Visual Basic). Nie są one udokumentowane niezależnie od ich klas bazowych, ponieważ ich zachowanie zostało opisane w dokumentacji klasy bazowej.  
  
<a name="related_topics"></a>   

## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Wyświetlanie informacji o typie](viewing-type-information.md)|Opisuje klasę <xref:System.Type> i zawiera przykłady kodu, które ilustrują sposób użycia <xref:System.Type> z kilkoma klasami odbicia w celu uzyskania informacji na temat konstruktorów, metod, pól, właściwości i zdarzeń.|  
|[Odbicie i typy ogólne](reflection-and-generic-types.md)|Wyjaśnia, jak odbicie obsługuje parametry typu i argumenty typu rodzajowego i metod ogólnych.|  
|[Zagadnienia dotyczące zabezpieczeń dla odbicia](security-considerations-for-reflection.md)|Opisuje reguły, które określają, w jakim stopniu odbicie może być używane do wykrywania informacji o typie i typów dostępu.|  
|[Dynamiczne ładowanie i używanie typów](dynamically-loading-and-using-types.md)|Opisuje interfejs powiązania niestandardowego odbicia obsługujący późne wiązanie.|  
|[Instrukcje: ładowanie zestawów do kontekstu Reflection-Only](how-to-load-assemblies-into-the-reflection-only-context.md)|Opisuje kontekst ładowania tylko odbicie. Pokazuje, jak załadować zestaw, jak przetestować kontekst i jak sprawdzać atrybuty zastosowane do zestawu w kontekście tylko odbicie.|  
|[Uzyskiwanie dostępu do atrybutów niestandardowych](accessing-custom-attributes.md)|Demonstruje użycie odbicia w celu uzyskania atrybutu i jego wartości.|  
|[Określanie w pełni kwalifikowanych nazw typów](specifying-fully-qualified-type-names.md)|Opisuje format w pełni kwalifikowanych nazw typów w warunkach Naura (BNF) i składni wymaganej do określenia znaków specjalnych, nazw zestawów, wskaźników, odwołań i tablic.|  
|[Instrukcje: podłączanie delegata za pomocą odbicia](how-to-hook-up-a-delegate-using-reflection.md)|Wyjaśnia, jak utworzyć delegata dla metody i podłączyć delegata do zdarzenia. Wyjaśnia, jak utworzyć metodę obsługi zdarzeń w czasie wykonywania przy użyciu <xref:System.Reflection.Emit.DynamicMethod>.|  
|[Emitowanie dynamicznych metod i zestawów](emitting-dynamic-methods-and-assemblies.md)|Wyjaśnia, jak generować dynamiczne zestawy i metody dynamiczne.|  
  
## <a name="reference"></a>Tematy pomocy  

<xref:System.Type?displayProperty=nameWithType>  
  
<xref:System.Reflection>  
  
<xref:System.Reflection.Emit>  
