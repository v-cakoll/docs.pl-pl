---
title: ':: operator - odwołanie do języka C#'
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
ms.openlocfilehash: a18e52ea05d49bf2b3a468923f1433f09fff9a8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712679"
---
# <a name="-operator-c-reference"></a>:: operator (odwołanie do Języka C#)

Użyj kwalifikatora `::` aliasu obszaru nazw, aby uzyskać dostęp do członka aliased namespace. Kwalifikatora `::` można używać tylko między dwoma identyfikatorami. Identyfikator po lewej stronie może być dowolny z następujących aliasów:

- Alias obszaru nazw utworzony przy [użyciu aliasdyrektywy:](../keywords/using-directive.md)

  ```csharp
  using forwinforms = System.Drawing;
  using forwpf = System.Windows;
  
  public class Converters
  {
      public static forwpf::Point Convert(forwinforms::Point point) => new forwpf::Point(point.X, point.Y);
  }
  ```

- Alias [extern](../keywords/extern-alias.md).
- Alias, `global` który jest aliasem globalnej przestrzeni nazw. Globalny obszar nazw to obszar nazw zawierający obszary nazw i typy, które nie są zadeklarowane wewnątrz nazwanego obszaru nazw. W przypadku `::` użycia z `global` kwalifikatorem alias zawsze odwołuje się do `global` globalnego obszaru nazw, nawet jeśli istnieje alias obszaru nazw zdefiniowany przez użytkownika.

  W poniższym `global` przykładzie użyto aliasu, aby uzyskać dostęp do obszaru nazw .NET, <xref:System> który jest członkiem globalnego obszaru nazw. Bez `global` aliasu można uzyskać `System` dostęp do obszaru nazw zdefiniowanego przez użytkownika, który jest członkiem obszaru `MyCompany.MyProduct` nazw:

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
  > Słowo `global` kluczowe jest aliasem globalnej przestrzeni nazw tylko wtedy, `::` gdy jest to lewy identyfikator kwalifikatora.

Można również użyć [operatora `.` dostępu do elementu członkowskiego,](member-access-operators.md#member-access-operator-) aby uzyskać dostęp do elementu członkowskiego aliased obszaru nazw. Jednak `.` operator jest również używany do uzyskiwania dostępu do elementu członkowskiego typu. Kwalifikator `::` zapewnia, że jego lewy identyfikator zawsze odwołuje się do aliasu obszaru nazw, nawet jeśli istnieje typ lub obszar nazw o tej samej nazwie.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [Kwalifikatory aliasu obszaru nazw](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- [Korzystanie z przestrzeni nazw](../../programming-guide/namespaces/using-namespaces.md)
