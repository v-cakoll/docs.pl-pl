---
ms.openlocfilehash: dc733ee32184db5af59bb06e294cd73765977581
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449566"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a>Element FieldInfo. SetValue zgłasza wyjątek dla pól static, tylko init

Począwszy od platformy .NET Core 3,0, wyjątek jest zgłaszany podczas próby ustawienia wartości w statycznej <xref:System.Reflection.FieldAttributes.InitOnly> polu przez wywołanie <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.

#### <a name="change-description"></a>Zmień opis

W .NET Framework i wersjach programu .NET Core wcześniejszych niż 3,0, można ustawić wartość pola statycznego, które jest stałe po zainicjowaniu ([ReadOnly in C# ](~/docs/csharp/language-reference/keywords/readonly.md)), wywołując <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>. Jednak ustawienie takiego pola w ten sposób skutkuje nieprzewidywalnym zachowaniem na podstawie ustawień platformy docelowej i optymalizacji.

W przypadku programu .NET Core 3,0 i jego nowszych wersji, gdy wywołasz <xref:System.Reflection.FieldInfo.SetValue%2A> w statycznej <xref:System.Reflection.FieldAttributes.InitOnly> polu, zostanie zgłoszony wyjątek <xref:System.FieldAccessException?displayProperty=nameWithType>.

> [!TIP]
> <xref:System.Reflection.FieldAttributes.InitOnly> pole to takie, które można ustawić tylko w czasie, gdy jest zadeklarowany, lub w konstruktorze dla klasy zawierającej. Innymi słowy, jest ona stała po zainicjowaniu.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Inicjuj statyczne <xref:System.Reflection.FieldAttributes.InitOnly> pól w konstruktorze statycznym. Dotyczy to zarówno typów dynamicznych, jak i niedynamicznych.

Alternatywnie możesz usunąć atrybut <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> z pola, a następnie wywołać <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>.

#### <a name="category"></a>Kategoria

CoreFx

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)?displayProperty=nameWithType>
- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)`
- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)`

-->
