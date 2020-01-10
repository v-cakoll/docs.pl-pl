---
title: ':: operator- C# odwołanie'
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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712679"
---
# <a name="-operator-c-reference"></a>:: — operatorC# (odwołanie)

Użyj kwalifikatora aliasu przestrzeni nazw `::`, aby uzyskać dostęp do elementu członkowskiego aliasu przestrzeni nazw. Kwalifikator `::` można użyć tylko między dwoma identyfikatorami. Identyfikator po lewej stronie może być jednym z następujących aliasów:

- Alias przestrzeni nazw utworzony za pomocą [dyrektywy aliasu using](../keywords/using-directive.md):

  ```csharp
  using forwinforms = System.Drawing;
  using forwpf = System.Windows;
  
  public class Converters
  {
      public static forwpf::Point Convert(forwinforms::Point point) => new forwpf::Point(point.X, point.Y);
  }
  ```

- [Alias zewnętrzny](../keywords/extern-alias.md).
- Alias `global`, który jest aliasem globalnym przestrzeni nazw. Globalna przestrzeń nazw jest przestrzenią nazw zawierającą przestrzenie nazw i typy, które nie są zadeklarowane w nazwanym obszarze nazw. Gdy jest używany z kwalifikatorem `::`, alias `global` zawsze odwołuje się do globalnej przestrzeni nazw, nawet jeśli istnieje `global` alias przestrzeni nazw zdefiniowany przez użytkownika.

  Poniższy przykład używa aliasu `global`, aby uzyskać dostęp do przestrzeni nazw .NET <xref:System>, która jest elementem członkowskim globalnej przestrzeni nazw. Bez aliasu `global` zdefiniowane przez użytkownika `System` przestrzeń nazw, która jest elementem członkowskim `MyCompany.MyProduct` przestrzeni nazw, zostanie uzyskany dostęp:

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
  > Słowo kluczowe `global` jest aliasem globalnym przestrzeni nazw tylko wtedy, gdy jest to identyfikator po lewej stronie kwalifikatora `::`.

Możesz również użyć [operatora `.` dostępu do elementu członkowskiego](member-access-operators.md#member-access-operator-) , aby uzyskać dostęp do elementu członkowskiego z aliasem. Jednak operator `.` jest również używany w celu uzyskania dostępu do elementu członkowskiego typu. Kwalifikator `::` gwarantuje, że jego identyfikator po lewej stronie zawsze odwołuje się do aliasu przestrzeni nazw, nawet jeśli istnieje typ lub przestrzeń nazw o tej samej nazwie.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [kwalifikatory aliasów przestrzeni nazw](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- [Używanie przestrzeni nazw](../../programming-guide/namespaces/using-namespaces.md)
