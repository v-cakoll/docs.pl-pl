---
title: Używanie typu dynamicznego (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic [C#], about dynamic type
- dynamic type [C#]
ms.assetid: 3828989d-c967-4a51-b948-857ebc8fdf26
ms.openlocfilehash: 296b9c80b4ea8b09e8efce71e3b388f7e453850b
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404379"
---
# <a name="using-type-dynamic-c-programming-guide"></a>Używanie typu dynamicznego (Przewodnik programowania w języku C#)
[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] wprowadza nowy typ `dynamic`. Typ jest typem statyczne, ale obiekt typu `dynamic` pomija sprawdzanie typu statycznego. W większości przypadków, funkcje, takie jak ma typ `object`. W czasie kompilacji, element, który jest `dynamic` założono, że obsługuje żadnych operacji. W związku z tym nie trzeba mieć wątpliwości dotyczące tego, czy obiekt wartość pochodzi z interfejsu API modelu COM, od języka dynamicznego, takich jak IronPython, z HTML Document Object Model (DOM), z odbicia lub gdzie indziej w programie. Jeśli kod nie jest prawidłowy, błędy są przechwytywane w czasie wykonywania.  
  
 Na przykład jeśli wystąpienie metody `exampleMethod1` w poniższym kodzie ma tylko jeden parametr, kompilator rozpoznaje, że pierwsze wywołanie do metody, `ec.exampleMethod1(10, 4)`, jest nieprawidłowy, ponieważ zawiera dwa argumenty. Wywołanie powoduje błąd kompilatora. Drugie wywołanie do metody, `dynamic_ec.exampleMethod1(10, 4)`, nie jest sprawdzana przez kompilator, ponieważ typ `dynamic_ec` jest `dynamic`. W związku z tym jest zgłaszany żaden błąd kompilatora. Jednak błąd nie zmienia znaczenia Zwróć uwagę na czas nieokreślony. On padł w czasie wykonywania i powoduje, że wyjątek czasu wykonywania.  
  
 [!code-csharp[CsProgGuideTypes#50](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_1.cs)]  
  
 [!code-csharp[CsProgGuideTypes#56](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_2.cs)]  
  
 Rola kompilatora w tych przykładach jest pakiet ze sobą informacje o każdej instrukcji proponowania do obiektu lub wyrażenie, które jest `dynamic`. W czasie wykonywania jest badany przechowywanych informacji, a żadnych instrukcji, która jest nieprawidłowa powoduje wyjątek czasu wykonywania.  
  
 Wynik operacji najbardziej dynamicznych jest sam `dynamic`. Na przykład, jeśli wskaźnik myszy nad użytkowania `testSum` w poniższym przykładzie funkcja IntelliSense wyświetla typ **testSum dynamiczna (zmienna lokalna)**.  
  
 [!code-csharp[CsProgGuideTypes#51](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_3.cs)]  
  
 Operacje, w których wynik nie jest `dynamic` obejmują:
 
* Konwersje z `dynamic` do innego typu. 
* Konstruktor wywołuje, które zawierają argumenty typu `dynamic`. 

Na przykład typ `testInstance` w następującej deklaracji jest `ExampleClass`, a nie `dynamic`:
  
 [!code-csharp[CsProgGuideTypes#52](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_4.cs)]  
  
 Przykłady konwersji są przedstawione w poniższej sekcji "Konwersje."  
  
## <a name="conversions"></a>Konwersje  
 Konwersje między obiektami dynamicznymi i inne typy są łatwe. Dzięki temu dla deweloperów przełączać się między zachowaniem dynamiczną i nie dynamicznych.  
  
 Każdy obiekt może można przekonwertować typu dynamicznego niejawnie, jak pokazano w poniższych przykładach.  
  
 [!code-csharp[CsProgGuideTypes#53](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_5.cs)]  
  
 Z drugiej strony, niejawna konwersja może dynamicznie stosowane do dowolnego wyrażenia typu `dynamic`.  
  
 [!code-csharp[CsProgGuideTypes#54](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_6.cs)]  
  
## <a name="overload-resolution-with-arguments-of-type-dynamic"></a>Rozpoznanie przeciążenia z argumentami typu dynamicznego  
 Rozpoznanie przeciążenia występuje w czasie wykonywania, a nie w czasie kompilacji, jeśli jeden lub więcej argumentów w wywołaniu metody ma typ `dynamic`, lub Jeśli odbiornik wywołania metody które jest typu `dynamic`. W poniższym przykładzie Jeśli dostępna tylko `exampleMethod2` zdefiniowano metody do wykonania argumentu ciągu wysyłania `d1` jako argument nie powoduje błąd kompilatora, ale to spowodować wyjątek czasu wykonywania. Rozpoznanie przeciążenia kończy się niepowodzeniem w czasie wykonywania, ponieważ typ środowiska wykonawczego `d1` jest `int`, i `exampleMethod2` wymaga ciągu.  
  
 [!code-csharp[CsProgGuideTypes#55](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_7.cs)]  
  
## <a name="dynamic-language-runtime"></a>Środowisko uruchomieniowe języka dynamicznego  
 Środowisko uruchomieniowe języka dynamicznego (DLR) jest nowy interfejs API w [!INCLUDE[net_v40_short](~/includes/net-v40-short-md.md)]. Zapewnia infrastrukturę, która obsługuje `dynamic` typ w języku C#, a także wykonania dynamicznego języków programowania, takich jak IronPython i IronRuby. Aby uzyskać więcej informacji na temat DLR zobacz [dynamiczny przegląd środowiska uruchomieniowego języka](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).  
  
## <a name="com-interop"></a>COM Interop  
 [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] zawiera kilka funkcji, które zwiększają możliwości współpracy z interfejsami API modelu COM, takich jak interfejsy API usługi Automation pakietu Office. Wśród ulepszenia są użytkowania `dynamic` typu i [argumentów nazwanych i opcjonalnych](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md).  
  
 Wiele metod COM Zezwalaj na zmianę w typy argumentów i typ zwracany przez wyznaczanie typy jako `object`. Jest to wymuszone jawne Rzutowanie wartości do zapewnienia koordynacji z silnie typizowanych zmiennych w języku C#. Jeśli kompilujesz przy użyciu [/Link (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/link-compiler-option.md) opcji wprowadzenia `dynamic` typu umożliwia traktowanie wystąpień `object` w podpisach COM tak, jakby były typu `dynamic`, a tym samym Aby uniknąć ilości rzutowania. Na przykład poniższe instrukcje kontrastu, sposób uzyskiwania dostępu do komórek w arkuszu kalkulacyjnym programu Microsoft Office Excel za pomocą `dynamic` typu i bez `dynamic` typu.  
  
 [!code-csharp[csOfficeWalkthrough#12](../../../csharp/programming-guide/interop/codesnippet/CSharp/using-type-dynamic_8.cs)]  
  
 [!code-csharp[csOfficeWalkthrough#13](../../../csharp/programming-guide/interop/codesnippet/CSharp/using-type-dynamic_9.cs)]  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[dynamic](../../../csharp/language-reference/keywords/dynamic.md)|W tym artykule opisano użycie `dynamic` — słowo kluczowe.|  
|[Przegląd środowiska uruchomieniowego języka dynamicznego](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)|Zawiera omówienie DLR, czyli środowiska uruchomieniowego, który dodaje zestaw usług dla języków dynamicznych do środowisko uruchomieniowe języka wspólnego (CLR).|  
|[Wskazówki: Tworzenie obiektów dynamicznych i posługiwanie](../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)|Instrukcje krok po kroku do tworzenia niestandardowych obiektów dynamicznych i do tworzenia projektu, który uzyskuje dostęp do `IronPython` biblioteki.|  
|[Instrukcje: uzyskiwanie dostępu do obiektów międzyoperacyjności pakietu Office za pomocą funkcji Visual C#](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)|Pokazuje, jak utworzyć projekt, który używa argumentów nazwanych i opcjonalnych, `dynamic` typu i inne rozszerzenia, które ułatwiają dostęp do obiektów interfejsu API usługi Office.|
