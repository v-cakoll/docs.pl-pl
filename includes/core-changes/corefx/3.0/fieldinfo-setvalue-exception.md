---
ms.openlocfilehash: 02c9305a36f47dfaf0b1fa8d19b07cd2d34badae
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721500"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a>Element FieldInfo. SetValue zgłasza wyjątek dla pól static, tylko init

Począwszy od platformy .NET Core 3,0, wyjątek jest zgłaszany podczas próby ustawienia wartości statycznego <xref:System.Reflection.FieldAttributes.InitOnly> pola przez wywołanie <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName> .

#### <a name="change-description"></a>Zmień opis

W .NET Framework i wersje programu .NET Core przed 3,0, można ustawić wartość pola statycznego, które jest stałe po zainicjowaniu ([ReadOnly w języku C#](~/docs/csharp/language-reference/keywords/readonly.md)) przez wywołanie metody <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName> . Jednak ustawienie takiego pola w ten sposób skutkuje nieprzewidywalnym zachowaniem na podstawie ustawień platformy docelowej i optymalizacji.

W przypadku programu .NET Core 3,0 i jego nowszych wersji, gdy wywoływana jest <xref:System.Reflection.FieldInfo.SetValue%2A> wartość statyczna <xref:System.Reflection.FieldAttributes.InitOnly> , <xref:System.FieldAccessException?displayProperty=nameWithType> zostanie zgłoszony wyjątek.

> [!TIP]
> <xref:System.Reflection.FieldAttributes.InitOnly>Pole to takie, które można ustawić tylko w czasie, gdy jest zadeklarowany, lub w konstruktorze dla klasy zawierającej. Innymi słowy, jest ona stała po zainicjowaniu.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Inicjuj statyczne <xref:System.Reflection.FieldAttributes.InitOnly> pola w konstruktorze statycznym. Dotyczy to zarówno typów dynamicznych, jak i niedynamicznych.

Alternatywnie możesz usunąć <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> atrybut z pola, a następnie wywołać metodę <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType> .

#### <a name="category"></a>Kategoria

Podstawowe biblioteki platformy .NET

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)?displayProperty=nameWithType>
- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)`
- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)`

-->
