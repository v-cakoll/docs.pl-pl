---
title: ':: operator - C#'
ms.date: 08/09/2019
f1_keywords:
- ::_CSharpKeyword
- global_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- namespace alias qualifier [C#]
- namespace [C#]
- global keyword [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 84c418627462f83630fe5072a0b0e2089f6588f6
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507129"
---
# <a name="-operator-c-reference"></a>:: operator (odwołanie C#)

Użyj kwalifikatora `::` aliasu obszaru nazw, aby uzyskać dostęp do członka aliasowanego obszaru nazw. `::` Kwalifikatora można używać tylko między dwoma identyfikatorami. Identyfikatorem po lewej stronie może być dowolny z następujących aliasów:

- Alias obszaru nazw utworzony przy [użyciu dyrektywy aliasu:](../keywords/using-directive.md)

  ```csharp
  using forwinforms = System.Drawing;
  using forwpf = System.Windows;
  
  public class Converters
  {
      public static forwpf::Point Convert(forwinforms::Point point) => new forwpf::Point(point.X, point.Y);
  }
  ```

- Alias [extern](../keywords/extern-alias.md).
- Alias, `global` który jest aliasem globalnej przestrzeni nazw. Globalna przestrzeń nazw to obszar nazw zawierający obszary nazw i typy, które nie są zadeklarowane w nazwanej przestrzeni nazw. W przypadku `::` użycia z `global` kwalifikatorem alias zawsze odwołuje się do `global` globalnej przestrzeni nazw, nawet jeśli istnieje alias obszaru nazw zdefiniowany przez użytkownika.

  W poniższym przykładzie użyto aliasu, `global` aby uzyskać dostęp do obszaru nazw platformy .NET, <xref:System> który jest członkiem globalnej przestrzeni nazw. Bez `global` aliasu dostęp do `System` zdefiniowanego przez użytkownika obszaru `MyCompany.MyProduct` nazw, który jest członkiem obszaru nazw, będzie dostępny:

  ```csharp
  namespace MyCompany.MyProduct.System
  {
      class Program
      {
          static void Main() => global::System.Console.WriteLine("Using global alias");
      }

      class Console
      {
          string Suggestion => "Consider renaming this class";
      }
  }
  ```

  > [!NOTE]
  > Słowo `global` kluczowe jest aliasem globalnej przestrzeni nazw tylko wtedy, `::` gdy jest to identyfikator po lewej stronie kwalifikatora.

Token można również [ `.` użyć,](member-access-operators.md#member-access-expression-) aby uzyskać dostęp do członka obszaru nazw o aliasie. Jednak `.` token jest również używany do dostępu do elementu członkowskiego typu. Kwalifikator `::` zapewnia, że jego identyfikator po lewej stronie zawsze odwołuje się do aliasu obszaru nazw, nawet jeśli istnieje typ lub obszar nazw o tej samej nazwie.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [Kwalifikatory aliasów obszaru nazw](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) [w specyfikacji języka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- [Korzystanie z obszarów nazw](../../programming-guide/namespaces/using-namespaces.md)
