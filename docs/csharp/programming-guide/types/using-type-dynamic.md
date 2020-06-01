---
title: Korzystanie z typu Dynamic-C# — Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic [C#], about dynamic type
- dynamic type [C#]
ms.assetid: 3828989d-c967-4a51-b948-857ebc8fdf26
ms.openlocfilehash: 24d48605e560038d70f1818611f339a94ecc2bba
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241971"
---
# <a name="using-type-dynamic-c-programming-guide"></a>Korzystanie z typu dynamicznego (Przewodnik programowania w języku C#)

W języku C# 4 wprowadzono nowy typ, `dynamic` . Typ jest typem statycznym, ale obiekt typu `dynamic` pomija sprawdzanie typu statycznego. W większości przypadków działa podobnie jak typ `object` . W czasie kompilacji element, który jest wpisywany jako `dynamic` jest przyjęty do obsługi dowolnej operacji. W związku z tym nie trzeba pamiętać o tym, czy obiekt pobiera swoją wartość z interfejsu API modelu COM, z dynamicznego języka, takiego jak IronPython, z Document Object Model HTML (DOM), z odbicia lub w innym miejscu w programie. Jeśli jednak kod jest nieprawidłowy, błędy są przechwytywane w czasie wykonywania.

Na przykład jeśli metoda wystąpienia `exampleMethod1` w poniższym kodzie ma tylko jeden parametr, kompilator rozpoznaje, że pierwsze wywołanie metody, `ec.exampleMethod1(10, 4)` , jest nieprawidłowe, ponieważ zawiera dwa argumenty. Wywołanie powoduje błąd kompilatora. Drugie wywołanie metody, `dynamic_ec.exampleMethod1(10, 4)` , nie jest sprawdzane przez kompilator, ponieważ typ `dynamic_ec` to `dynamic` . W związku z tym nie jest raportowany żaden błąd kompilatora. Niemniej jednak w przypadku błędu nie jest to zauważalne. Jest przechwytywany w czasie wykonywania i powoduje wyjątek w czasie wykonywania.

[!code-csharp[CsProgGuideTypes#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#50)]

[!code-csharp[CsProgGuideTypes#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#56)]

Rolą kompilatora w tych przykładach jest spakowanie informacji o tym, co zaproponowają poszczególne instrukcje do obiektu lub wyrażenia, które jest wpisane jako `dynamic` . W czasie wykonywania są badane przechowywane informacje, a wszelkie nieprawidłowe instrukcje powodują wyjątek w czasie wykonywania.

Wynik większości operacji dynamicznych jest sam `dynamic` . Na przykład, jeśli umieścisz wskaźnik myszy nad użyciem `testSum` w poniższym przykładzie, IntelliSense wyświetla typ **(zmienna lokalna) Dynamic testSum**.

[!code-csharp[CsProgGuideTypes#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#51)]

Operacje, w których wynik nie jest `dynamic` uwzględniany:

* Konwersje od `dynamic` do innego typu.
* Wywołania konstruktora, które zawierają argumenty typu `dynamic` .

Na przykład typ `testInstance` w następującej deklaracji to `ExampleClass` , nie `dynamic` :

[!code-csharp[CsProgGuideTypes#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#52)]

Przykłady konwersji przedstawiono w poniższej sekcji "Konwersje".

## <a name="conversions"></a>Konwersje

Konwersje między obiektami dynamicznymi i innymi typami są łatwe. Dzięki temu deweloper może przełączać się między zachowaniem dynamicznym a niedynamicznym.

Każdy obiekt można przekonwertować na typ dynamiczny niejawnie, jak pokazano w poniższych przykładach.

[!code-csharp[CsProgGuideTypes#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#53)]

Z kolei niejawna konwersja może być dynamicznie stosowana do dowolnego wyrażenia typu `dynamic` .

[!code-csharp[CsProgGuideTypes#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#54)]

## <a name="overload-resolution-with-arguments-of-type-dynamic"></a>Rozpoznanie przeciążenia z argumentami typu dynamicznego

Rozwiązanie przeciążania występuje w czasie wykonywania, a nie w czasie kompilacji, jeśli co najmniej jeden z argumentów w wywołaniu metody ma typ `dynamic` lub odbiorca wywołania metody jest typu `dynamic` . W poniższym przykładzie, jeśli jedyną dostępną `exampleMethod2` metodą jest zdefiniowanie argumentu String, wysłanie `d1` jako argument nie powoduje błędu kompilatora, ale powoduje wyjątek w czasie wykonywania. Rozpoznanie przeciążenia nie powiodło się w czasie wykonywania, ponieważ typ czasu wykonywania `d1` to `int` i `exampleMethod2` wymaga ciągu.

[!code-csharp[CsProgGuideTypes#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#55)]

## <a name="dynamic-language-runtime"></a>Środowisko uruchomieniowe języka dynamicznego

Środowisko uruchomieniowe języka dynamicznego (DLR) jest interfejsem API, który został wprowadzony w .NET Framework 4. Zapewnia infrastrukturę, która obsługuje `dynamic` Typ w języku C#, a także implementację dynamicznych języków programowania, takich jak IronPython i IronRuby. Aby uzyskać więcej informacji na temat DLR, zobacz [Omówienie środowiska uruchomieniowego języka dynamicznego](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).

## <a name="com-interop"></a>COM interop

Język C# 4 zawiera kilka funkcji, które zwiększają możliwości współpracy z interfejsami API modelu COM, takimi jak interfejsy API usługi Office Automation. Wśród ulepszeń są użycie `dynamic` typu i [argumentów nazwanych i opcjonalnych](../classes-and-structs/named-and-optional-arguments.md).

Wiele metod COM pozwala na odchylenia typów argumentów i zwracanego typu przez wyznaczenie typów jako `object` . Jest to konieczne jawne rzutowanie wartości w celu współrzędnych z silnie wpisanąmi zmiennymi w języku C#. Jeśli kompilujesz przy użyciu opcji [-link (opcje kompilatora C#)](../../language-reference/compiler-options/link-compiler-option.md) , wprowadzenie `dynamic` typu umożliwia traktowanie wystąpień `object` w sygnaturach com, tak jakby były typu `dynamic` , i tym samym, aby uniknąć zbyt dużej ilości rzutowania. Na przykład następujące instrukcje różnią się, jak uzyskać dostęp do komórki w Microsoft Office arkuszu kalkulacyjnym programu Excel z `dynamic` typem i bez `dynamic` typu.

[!code-csharp[csOfficeWalkthrough#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#12)]

[!code-csharp[csOfficeWalkthrough#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#13)]

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[dynamiczna](../../language-reference/builtin-types/reference-types.md)|Opisuje użycie `dynamic` słowa kluczowego.|
|[Omówienie środowiska uruchomieniowego języka dynamicznego](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)|Zawiera omówienie DLR, czyli środowisko uruchomieniowe, które dodaje zestaw usług dla języków dynamicznych do środowiska uruchomieniowego języka wspólnego (CLR).|
|[Przewodnik: Tworzenie obiektów dynamicznych i korzystanie z nich](walkthrough-creating-and-using-dynamic-objects.md)|Zawiera instrukcje krok po kroku dotyczące tworzenia niestandardowego obiektu dynamicznego i tworzenia projektu, który uzyskuje dostęp do `IronPython` biblioteki.|
|[Uzyskiwanie dostępu do obiektów międzyoperacyjności pakietu Office za pomocą funkcji języka C#](../interop/how-to-access-office-onterop-objects.md)|Pokazuje, jak utworzyć projekt, który używa argumentów nazwanych i opcjonalnych, `dynamic` typu i innych ulepszeń, które upraszczają dostęp do obiektów interfejsu API pakietu Office.|
