---
title: "Używanie typu dynamicznego (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- dynamic [C#], about dynamic type
- dynamic type [C#]
ms.assetid: 3828989d-c967-4a51-b948-857ebc8fdf26
caps.latest.revision: "30"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e4eea7cd1bf87ac4c4efb827e6a9ca403e94acc9
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2017
---
# <a name="using-type-dynamic-c-programming-guide"></a>Używanie typu dynamicznego (Przewodnik programowania w języku C#)
[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)]został wprowadzony nowy typ `dynamic`. Typ jest typ statyczny, ale obiekt typu `dynamic` pomija sprawdzanie typu statycznego. W większości przypadków, funkcje, takie jak ma typ `object`. W czasie kompilacji, element, który jest typu `dynamic` przyjęto, że do żadnej operacji obsługi. W związku z tym nie trzeba mieć na uwadze Określa, czy obiekt wartość pochodzi z interfejsu API modelu COM, z języka dynamicznego, takich jak IronPython, z HTML modelu DOM (Document Object), z odbicia lub w innym miejscu w programie. Jeśli kod jest nieprawidłowy, błędy są przechwytywane w czasie wykonywania.  
  
 Na przykład jeśli metoda wystąpienia `exampleMethod1` w poniższym kodzie ma tylko jeden parametr, kompilator rozpoznaje, że pierwsze wywołanie do metody, `ec.exampleMethod1(10, 4)`, jest nieprawidłowy, ponieważ zawiera dwa argumenty. Wywołanie powoduje błąd kompilatora. Drugie wywołanie do metody, `dynamic_ec.exampleMethod1(10, 4)`, nie jest sprawdzana przez kompilator, ponieważ typ `dynamic_ec` jest `dynamic`. W związku z tym nie kompilator będzie zgłaszany błąd. Jednak błąd nie escape powiadomień przez nieograniczony czas. Ten program zostanie przechwycony w czasie wykonywania i powoduje, że wyjątek czasu wykonywania.  
  
 [!code-csharp[CsProgGuideTypes#50](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_1.cs)]  
  
 [!code-csharp[CsProgGuideTypes#56](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_2.cs)]  
  
 Rola kompilatora w tych przykładach jest pakiet ze sobą informacje o każdej instrukcji proponowania do obiektu lub wyrażenie, które jest typu `dynamic`. W czasie wykonywania przechowywane informacje się zbadana i żadnych instrukcji, która nie jest prawidłową powoduje, że wyjątek czasu wykonywania.  
  
 Wynik operacji najbardziej dynamicznych jest `dynamic`. Na przykład, jeśli wskaźnik myszy nad stosowania `testSum` w poniższym przykładzie funkcja IntelliSense wyświetla typ **testSum dynamiczna (zmienna lokalna)**.  
  
 [!code-csharp[CsProgGuideTypes#51](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_3.cs)]  
  
 Operacje, w których nie jest `dynamic` obejmują konwersje z `dynamic` do innego typu, a wywołania konstruktora, które obejmują argumenty typu `dynamic`. Na przykład typ `testInstance` w następujących deklaracji jest `ExampleClass`, a nie `dynamic`.  
  
 [!code-csharp[CsProgGuideTypes#52](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_4.cs)]  
  
 Przykłady konwersji są przedstawione w poniższej sekcji "Konwersje."  
  
## <a name="conversions"></a>Konwersje  
 Konwersje między obiektami dynamicznymi i inne typy są łatwe. Umożliwia to deweloperom przełączania się między zachowanie dynamicznych i -dynamic.  
  
 Każdy obiekt może zostać przekonwertowany do typu dynamicznego niejawnie, jak pokazano w poniższych przykładach.  
  
 [!code-csharp[CsProgGuideTypes#53](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_5.cs)]  
  
 Z drugiej strony, niejawna konwersja mogą być dynamicznie stosowane do dowolnego wyrażenia typu `dynamic`.  
  
 [!code-csharp[CsProgGuideTypes#54](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_6.cs)]  
  
## <a name="overload-resolution-with-arguments-of-type-dynamic"></a>Rozpoznanie przeciążenia z argumentami typu dynamicznego  
 Rozpoznanie przeciążenia występuje w czasie wykonywania, a nie w czasie kompilacji, jeśli jeden lub więcej argumentów w wywołaniu metody ma typ `dynamic`, lub Jeśli odbiornik wywołania metody jest typu `dynamic`. W poniższym przykładzie Jeśli dostępna tylko `exampleMethod2` metody zdefiniowano podjęcie argument ciągu, wysyłanie `d1` jako argument nie powoduje błąd kompilatora, ale spowodować wyjątek czasu wykonywania. Rozpoznanie przeciążenia nie działa w czasie wykonywania, ponieważ typ środowiska wykonawczego `d1` jest `int`, i `exampleMethod2` wymaga parametrów.  
  
 [!code-csharp[CsProgGuideTypes#55](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_7.cs)]  
  
## <a name="dynamic-language-runtime"></a>Środowisko uruchomieniowe języka dynamicznego  
 Środowisko uruchomieniowe języka dynamicznego (DLR) to nowy interfejs API w [!INCLUDE[net_v40_short](~/includes/net-v40-short-md.md)]. Zapewnia infrastrukturę, która obsługuje `dynamic` typu w języku C#, a także wykonania dynamiczne języków programowania, takich jak IronPython i IronRuby. Aby uzyskać więcej informacji na temat DLR, zobacz [Przegląd środowiska uruchomieniowego języka dynamicznego](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).  
  
## <a name="com-interop"></a>COM Interop  
 [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)]zawiera kilka funkcji, które sprawniej współpracy z interfejsów API modelu COM., takich jak Office API automatyzacji. Wśród ulepszenia jest używanie `dynamic` typu i [argumenty nazwane i opcjonalne](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md).  
  
 Wiele metod COM umożliwić zmienność typy argumentów i typ zwracany przez wyznaczenie typy jako `object`. Ma to wymuszone jawne Rzutowanie wartości do zapewnienia koordynacji z jednoznacznie zmiennych w języku C#. Jeśli skompilować przy użyciu [/Link (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/link-compiler-option.md) opcję wprowadzenia `dynamic` typu umożliwia Traktuj wystąpień `object` w podpisach COM tak, jakby były typu `dynamic`i tym samym Aby uniknąć znacznie rzutowania. Na przykład następujące instrukcje kontrast, jak uzyskać dostępu do komórki w arkuszu kalkulacyjnym programu Microsoft Office Excel z `dynamic` typu i bez `dynamic` typu.  
  
 [!code-csharp[csOfficeWalkthrough#12](../../../csharp/programming-guide/interop/codesnippet/CSharp/using-type-dynamic_8.cs)]  
  
 [!code-csharp[csOfficeWalkthrough#13](../../../csharp/programming-guide/interop/codesnippet/CSharp/using-type-dynamic_9.cs)]  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[dynamiczne](../../../csharp/language-reference/keywords/dynamic.md)|W tym artykule opisano użycie `dynamic` — słowo kluczowe.|  
|[Omówienie środowiska uruchomieniowego języka dynamicznego](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)|Zawiera omówienie Runtime, czyli środowiska uruchomieniowego, który dodaje zestaw usług dla języków dynamicznych do środowisko uruchomieniowe języka wspólnego (CLR).|  
|[Wskazówki: Tworzenie obiektów dynamicznych i posługiwanie](../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)|Instrukcje krok po kroku dotyczące tworzenia niestandardowych obiektów dynamicznych i tworzenia projektu, który uzyskuje dostęp do `IronPython` biblioteki.|  
|[Porady: dostęp do obiektów międzyoperacyjności pakietu Office za pomocą funkcji Visual C#](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)|Pokazuje, jak utworzyć projekt, który używa argumentów nazwanych i opcjonalnych, `dynamic` typu i inne rozszerzenia, które ułatwiają dostęp do interfejsu API usługi Office obiektów.|
