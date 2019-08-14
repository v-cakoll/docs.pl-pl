---
title: ':: operator- C# odwołanie'
ms.custom: seodec18
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
ms.openlocfilehash: 2aceb51747708b12fb3059b097b72206c78a9d5d
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971244"
---
# <a name="-operator-c-reference"></a>:: — operatorC# (odwołanie)

Użyj kwalifikatora `::` aliasu przestrzeni nazw, aby uzyskać dostęp do elementów członkowskich z aliasem przestrzeni nazw. `::` Kwalifikator jest używany między dwoma identyfikatorami. Identyfikator po lewej stronie może być jednym z następujących aliasów:

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
- `global` Alias, który jest aliasem globalnym przestrzeni nazw. Globalna przestrzeń nazw jest przestrzenią nazw zawierającą przestrzenie nazw i typy, które nie są zadeklarowane w nazwanym obszarze nazw. Gdy jest używany z `::` kwalifikatorem `global` , alias zawsze odwołuje się do globalnej przestrzeni nazw, nawet jeśli istnieje alias przestrzeni nazw `global` zdefiniowany przez użytkownika.
  
  Poniższy przykład używa `global` aliasu, aby uzyskać dostęp do <xref:System> przestrzeni nazw .NET, która jest elementem członkowskim globalnej przestrzeni nazw. Bez aliasu zdefiniowana `System` przez użytkownika przestrzeń nazw, która `MyCompany.MyProduct` jest członkiem przestrzeni nazw, zostanie uzyskany dostęp: `global`

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
  > Słowo kluczowe jest aliasem globalnym przestrzeni nazw tylko wtedy, gdy jest to identyfikator `::` po lewej stronie kwalifikatora. `global`

Możesz również użyć [operatora `.` dostępu do elementów członkowskich](member-access-operators.md#member-access-operator-) , aby uzyskać dostęp do elementów członkowskich z aliasem. `.` Jednak operator jest również używany do uzyskiwania dostępu do elementów członkowskich typu. `::` Kwalifikator gwarantuje, że jego identyfikator po lewej stronie zawsze odwołuje się do aliasu przestrzeni nazw, nawet jeśli istnieje typ lub przestrzeń nazw o tej samej nazwie.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [kwalifikatory aliasów przestrzeni nazw](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- [Używanie przestrzeni nazw](../../programming-guide/namespaces/using-namespaces.md)
