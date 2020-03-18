---
title: Korzystanie z funkcji dynamicznych typów — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic [C#], about dynamic type
- dynamic type [C#]
ms.assetid: 3828989d-c967-4a51-b948-857ebc8fdf26
ms.openlocfilehash: c5ac5b3692266010f0be8672ef744baaa32e6a03
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75711860"
---
# <a name="using-type-dynamic-c-programming-guide"></a>Korzystanie z typu dynamicznego (Przewodnik programowania C#)

C# 4 wprowadza nowy `dynamic`typ, . Typ jest typem statycznym, ale `dynamic` obiekt typu pomija statyczne sprawdzanie typu. W większości przypadków działa tak, `object`jakby miał typ . W czasie kompilacji element, który `dynamic` jest wpisany zgodnie z założeniem, że obsługuje dowolną operację. W związku z tym nie trzeba się martwić o to, czy obiekt pobiera jego wartość z interfejsu API MODELU, z języka dynamicznego, takiego jak IronPython, z modelu obiektu dokumentu HTML (DOM), z odbicia lub z innego miejsca w programie. Jednak jeśli kod jest nieprawidłowy, błędy są przechwycone w czasie wykonywania.

Na przykład jeśli `exampleMethod1` metoda wystąpienia w poniższym kodzie ma tylko jeden parametr, kompilator rozpoznaje, że pierwsze wywołanie metody , jest nieprawidłowy, `ec.exampleMethod1(10, 4)`ponieważ zawiera dwa argumenty. Wywołanie powoduje błąd kompilatora. Drugie wywołanie metody `dynamic_ec.exampleMethod1(10, 4)`, nie jest sprawdzane przez kompilator, ponieważ typem `dynamic_ec` jest `dynamic`. W związku z tym nie jest zgłaszany błąd kompilatora. Jednak błąd nie uniknie powiadomienia na czas nieokreślony. Jest on przechwycony w czasie wykonywania i powoduje wyjątek w czasie wykonywania.

[!code-csharp[CsProgGuideTypes#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#50)]

[!code-csharp[CsProgGuideTypes#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#56)]

Rola kompilatora w tych przykładach jest pakiet razem informacje o tym, co każda instrukcja `dynamic`proponuje zrobić do obiektu lub wyrażenia, który jest wpisany jako . W czasie wykonywania przechowywane informacje są sprawdzane, a każda instrukcja, która jest nieprawidłowa powoduje wyjątek w czasie wykonywania.

Wynikiem najbardziej dynamicznych operacji `dynamic`jest sam . Na przykład jeśli wskaźnik myszy zostanie oparcie na użycie `testSum` w poniższym przykładzie, IntelliSense wyświetla typ **(zmienna lokalna) dynamic testSum**.

[!code-csharp[CsProgGuideTypes#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#51)]

Operacje, w których `dynamic` wynik nie obejmuje:

* Konwersje `dynamic` z innego typu.
* Wywołania konstruktora, `dynamic`które zawierają argumenty typu .

Na przykład typ `testInstance` w następującej `ExampleClass`deklaracji `dynamic`jest , nie:

[!code-csharp[CsProgGuideTypes#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#52)]

Przykłady konwersji są wyświetlane w poniższej sekcji "Konwersje".

## <a name="conversions"></a>Konwersje

Konwersje między obiektami dynamicznymi a innymi typami są łatwe. Dzięki temu deweloper przełączać się między zachowaniem dynamicznym i niedynamicznym.

Każdy obiekt można przekonwertować na typ dynamiczny niejawnie, jak pokazano w poniższych przykładach.

[!code-csharp[CsProgGuideTypes#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#53)]

Z drugiej strony konwersja niejawna może być `dynamic`dynamicznie stosowana do dowolnego wyrażenia typu .

[!code-csharp[CsProgGuideTypes#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#54)]

## <a name="overload-resolution-with-arguments-of-type-dynamic"></a>Rozpoznawanie przeciążeń z argumentami typu dynamicznego

Rozpoznawanie przeciążenia występuje w czasie wykonywania, a nie w czasie kompilacji, jeśli jeden lub więcej argumentów w wywołaniu metody mają typ `dynamic`, lub jeśli odbiorca wywołania metody jest typu `dynamic`. W poniższym przykładzie, jeśli `exampleMethod2` tylko dostępna metoda jest zdefiniowana do podjęcia argument ciąg, wysyłanie `d1` jako argument nie powoduje błąd kompilatora, ale powoduje wyjątek w czasie wykonywania. Rozpoznawanie przeciążenia kończy się niepowodzeniem `d1` w `int`czasie `exampleMethod2` wykonywania, ponieważ typ czasu wykonywania jest , i wymaga ciągu.

[!code-csharp[CsProgGuideTypes#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#55)]

## <a name="dynamic-language-runtime"></a>Dynamiczny czas uruchomieniowy języka

Dynamiczny program uruchamiany języka (DLR) to nowy interfejs API w .NET Framework 4. Zapewnia infrastrukturę, która `dynamic` obsługuje typ w języku C#, a także implementację dynamicznych języków programowania, takich jak IronPython i IronRuby. Aby uzyskać więcej informacji na temat dlr, zobacz [Omówienie wykonywania języka dynamicznego](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).

## <a name="com-interop"></a>COM interop

C# 4 zawiera kilka funkcji, które poprawiają środowisko współdziałania z interfejsami API COM, takich jak interfejsy API automatyzacji pakietu Office. Wśród ulepszeń są użycie `dynamic` typu oraz [nazwanych i opcjonalnych argumentów](../classes-and-structs/named-and-optional-arguments.md).

Wiele metod COM pozwala na różnice w typach argumentów `object`i typ zwracany, wyznaczając typy jako . Wymagało to jawnego rzutowania wartości do koordynacji ze zmiennymi silnie typizowane w języku C#. Jeśli skompilować przy użyciu [-link (Opcje kompilatora C#),](../../language-reference/compiler-options/link-compiler-option.md) wprowadzenie `dynamic` tego typu `object` umożliwia traktować wystąpienia w `dynamic`podpisy COM, jak gdyby były typu, a tym samym uniknąć wiele rzutowania. Na przykład następujące instrukcje kontrastują sposób uzyskiwania dostępu do `dynamic` komórki w `dynamic` arkuszu kalkulacyjnym programu Microsoft Office Excel z typem i bez typu.

[!code-csharp[csOfficeWalkthrough#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#12)]

[!code-csharp[csOfficeWalkthrough#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#13)]

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Dynamiczne](../../language-reference/builtin-types/reference-types.md)|Opisuje użycie słowa `dynamic` kluczowego.|
|[Omówienie czasu wykonywania języka dynamicznego](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)|Zawiera omówienie dlr, który jest środowiskiem środowiska uruchomieniowego, który dodaje zestaw usług dla języków dynamicznych do środowiska uruchomieniowego języka wspólnego (CLR).|
|[Instruktaż: Tworzenie i używanie obiektów dynamicznych](walkthrough-creating-and-using-dynamic-objects.md)|Zawiera instrukcje krok po kroku dotyczące tworzenia niestandardowego obiektu dynamicznego i `IronPython` tworzenia projektu, który uzyskuje dostęp do biblioteki.|
|[Uzyskiwanie dostępu do obiektów międzyoperacyjności pakietu Office za pomocą funkcji języka C#](../interop/how-to-access-office-onterop-objects.md)|Pokazuje, jak utworzyć projekt, który używa nazwanych i opcjonalnych argumentów, `dynamic` typu i innych ulepszeń, które upraszczają dostęp do obiektów interfejsu API pakietu Office.|
