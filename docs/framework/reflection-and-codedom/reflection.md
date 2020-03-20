---
title: Odbicie w .NET
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
ms.openlocfilehash: 90d9cf4c473d73d1eeeb5f2a1098f8626c20359f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180473"
---
# <a name="reflection-in-net"></a>Odbicie w .NET

Klasy w <xref:System.Reflection> obszarze nazw, <xref:System.Type?displayProperty=nameWithType>wraz z , umożliwiają uzyskanie informacji o załadowanych [zestawach](../../standard/assembly/index.md) i typów zdefiniowanych w nich, takich jak [klasy,](../../standard/base-types/common-type-system.md#classes) [interfejsy](../../standard/base-types/common-type-system.md#interfaces)i typy wartości (czyli struktury i [wyliczenia](../../standard/base-types/common-type-system.md#enumerations)). [structures](../../standard/base-types/common-type-system.md#structures) Można również użyć odbicia do tworzenia wystąpień typu w czasie wykonywania i do wywoływania i uzyskiwania do nich dostępu. Aby zapoznać się z tematami dotyczącymi określonych aspektów refleksji, zobacz [Tematy pokrewne](#related_topics) na końcu tego przeglądu.
  
Program ładujący [środowiska wykonawczego języka wspólnego](../../standard/clr.md) zarządza [domenami aplikacji,](../app-domains/application-domains.md)które stanowią zdefiniowane granice wokół obiektów, które mają ten sam zakres aplikacji. To zarządzanie obejmuje ładowanie każdego zestawu do odpowiedniej domeny aplikacji i kontrolowanie układu pamięci hierarchii typów w każdym zestawie.  
  
[Zestawy](../app-domains/index.md) zawierają moduły, moduły zawierają typy, a typy zawierają elementy członkowskie. Odbicie zapewnia obiekty, które hermetyzują złożenia, moduły i typy. Odbicie służy do dynamicznego tworzenia wystąpienia typu, powiązania typu z istniejącym obiektem lub uzyskania typu z istniejącego obiektu. Następnie można wywołać metody typu lub uzyskać dostęp do jego pól i właściwości. Typowe zastosowania odbicia są następujące:  
  
- Służy <xref:System.Reflection.Assembly> do definiowania i ładowania złożeń, ładowania modułów wymienionych w manifeście złożenia i lokalizowania typu z tego złożenia i tworzenia jego wystąpienia.  
  
- Służy <xref:System.Reflection.Module> do odnajdywać informacje, takie jak zestaw, który zawiera moduł i klas w module. Można również uzyskać wszystkie metody globalne lub inne specyficzne, nieglobalne metody zdefiniowane w module.  
  
- Służy <xref:System.Reflection.ConstructorInfo> do odnajdowania informacji, takich jak `public` nazwa, parametry, modyfikatory dostępu (takie jak lub `private`) i szczegóły implementacji (takie jak `abstract` lub) `virtual`konstruktora. Użyj <xref:System.Type.GetConstructors%2A> lub <xref:System.Type.GetConstructor%2A> metody <xref:System.Type> a wywołać określonego konstruktora.  
  
- Służy <xref:System.Reflection.MethodInfo> do odnajdowania informacji, takich jak nazwa, `public` typ `private`zwracany, parametry, `abstract` `virtual`modyfikatory dostępu (takie jak lub ) i szczegóły implementacji (takie jak lub) metody. Użyj <xref:System.Type.GetMethods%2A> lub <xref:System.Type.GetMethod%2A> metody <xref:System.Type> a wywołać określoną metodę.  
  
- Służy <xref:System.Reflection.FieldInfo> do odnajdywać informacje, takie `public` `private`jak nazwa, modyfikatory dostępu (takie jak lub) i szczegóły implementacji (takie jak) `static`pola oraz uzyskać lub ustawić wartości pól.  
  
- Służy <xref:System.Reflection.EventInfo> do odnajdowania informacji, takich jak nazwa, typ danych obsługi zdarzeń, atrybuty niestandardowe, deklarowanie typu i odzwierciedlenie typu zdarzenia oraz do dodawania lub usuwania programów obsługi zdarzeń.  
  
- Służy <xref:System.Reflection.PropertyInfo> do odnajdowania informacji, takich jak nazwa, typ danych, deklarowanie typu, typ odzwierciedlenie i tylko do odczytu lub zapisywalny stan właściwości, a także do uzyskania lub ustawiania wartości właściwości.  
  
- Służy <xref:System.Reflection.ParameterInfo> do odnajdowania informacji, takich jak nazwa parametru, typ danych, czy parametr jest parametrem wejściowym lub wyjściowym oraz położenie parametru w podpisie metody.  
  
- Służy <xref:System.Reflection.CustomAttributeData> do odnajdywać informacje o atrybutach niestandardowych podczas pracy w kontekście tylko do odbicia domeny aplikacji. <xref:System.Reflection.CustomAttributeData>umożliwia badanie atrybutów bez tworzenia ich wystąpień.  
  
Klasy obszaru <xref:System.Reflection.Emit> nazw zapewniają wyspecjalizowaną formę odbicia, która umożliwia tworzenie typów w czasie wykonywania.  
  
Odbicie może być również używane do tworzenia aplikacji o nazwie przeglądarki typów, które umożliwiają użytkownikom wybieranie typów, a następnie wyświetlanie informacji o tych typach.  
  
Istnieją inne zastosowania do refleksji. Kompilatory dla języków, takich jak JScript używać odbicia do konstruowania tabel symboli. Klasy w <xref:System.Runtime.Serialization> obszarze nazw używają odbicia, aby uzyskać dostęp do danych i określić, które pola mają być zachowywane. Klasy w <xref:System.Runtime.Remoting> obszarze nazw używać odbicia pośrednio poprzez serializacji.  
  
## <a name="runtime-types-in-reflection"></a>Typy środowiska uruchomieniowego w odbiciu  
Odbicie zapewnia klasy, takie jak <xref:System.Type> i <xref:System.Reflection.MethodInfo>, do reprezentowania typów, elementów członkowskich, parametrów i innych jednostek kodu. Jednak podczas korzystania z odbicia, nie działają bezpośrednio z tych klas,`MustInherit` z których większość jest abstrakcyjna (w języku Visual Basic). Zamiast tego pracujesz z typami dostarczonymi przez środowisko uruchomieniowe języka wspólnego (CLR).  
  
Na przykład podczas korzystania z `typeof` operatora`GetType` C# (w <xref:System.Type> języku Visual Basic) `RuntimeType`w celu uzyskania obiektu, obiekt jest naprawdę . `RuntimeType`pochodzi z <xref:System.Type> i zapewnia implementacje wszystkich metod abstrakcyjnych.  
  
Te klasy środowiska `internal` `Friend` uruchomieniowego są ( w języku Visual Basic). Nie są one udokumentowane oddzielnie od ich klas podstawowych, ponieważ ich zachowanie jest opisane przez dokumentację klasy podstawowej.  
  
<a name="related_topics"></a>

## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Wyświetlanie informacji o typie](viewing-type-information.md)|W <xref:System.Type> tym artykule opisano klasę i zawiera <xref:System.Type> przykłady kodu, które ilustrują, jak używać z kilkoma klasami odbicia w celu uzyskania informacji o konstruktorach, metodach, polach, właściwościach i zdarzeniach.|  
|[Odbicie i typy ogólne](reflection-and-generic-types.md)|Wyjaśniono, jak odbicie obsługuje parametry typu i argumenty typu typów ogólnych i metod ogólnych.|  
|[Zagadnienia dotyczące zabezpieczeń dla odbicia](security-considerations-for-reflection.md)|W tym artykule opisano reguły, które określają, w jakim stopniu odbicie może służyć do odnajdowania informacji o typie i typów dostępu.|  
|[Dynamiczne ładowanie i używanie typów](dynamically-loading-and-using-types.md)|W tym artykule opisano interfejs niestandardowego powiązania odbicia, który obsługuje późne powiązanie.|  
|[Porady: ładowanie zestawów do kontekstu Reflection-Only](how-to-load-assemblies-into-the-reflection-only-context.md)|Opisuje kontekst ładowania tylko do odbicia. Pokazuje, jak załadować zestaw, jak przetestować kontekst i jak sprawdzić atrybuty zastosowane do zestawu w kontekście tylko do odbicia.|  
|[Uzyskiwanie dostępu do atrybutów niestandardowych](accessing-custom-attributes.md)|Pokazuje za pomocą odbicia do kwerendy atrybut istnienia i wartości.|  
|[Określanie w pełni kwalifikowanych nazw typów](specifying-fully-qualified-type-names.md)|Opisuje format w pełni kwalifikowanych nazw typów w postaci formularza Backus-Naur (BNF) oraz składnię wymaganą do określania znaków specjalnych, nazw zestawów, wskaźników, odwołań i tablic.|  
|[Porady: podłączanie delegata za pomocą odbicia](how-to-hook-up-a-delegate-using-reflection.md)|Wyjaśniono, jak utworzyć pełnomocnika dla metody i podłączyć pełnomocnika do zdarzenia. W tym artykule wyjaśniono, jak <xref:System.Reflection.Emit.DynamicMethod>utworzyć metodę obsługi zdarzeń w czasie wykonywania przy użyciu programu .|  
|[Emitowanie dynamicznych metod i zestawów](emitting-dynamic-methods-and-assemblies.md)|Wyjaśniono, jak generować zestawy dynamiczne i metody dynamiczne.|  
  
## <a name="reference"></a>Dokumentacja  

<xref:System.Type?displayProperty=nameWithType>  
  
<xref:System.Reflection>  
  
<xref:System.Reflection.Emit>  
