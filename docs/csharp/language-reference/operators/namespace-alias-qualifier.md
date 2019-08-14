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
# <a name="-operator-c-reference"></a><span data-ttu-id="14e18-102">:: — operatorC# (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="14e18-102">:: operator (C# reference)</span></span>

<span data-ttu-id="14e18-103">Użyj kwalifikatora `::` aliasu przestrzeni nazw, aby uzyskać dostęp do elementów członkowskich z aliasem przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="14e18-103">Use the namespace alias qualifier `::` to access members of an aliased namespace.</span></span> <span data-ttu-id="14e18-104">`::` Kwalifikator jest używany między dwoma identyfikatorami.</span><span class="sxs-lookup"><span data-stu-id="14e18-104">You use the `::` qualifier between two identifiers.</span></span> <span data-ttu-id="14e18-105">Identyfikator po lewej stronie może być jednym z następujących aliasów:</span><span class="sxs-lookup"><span data-stu-id="14e18-105">The left-hand identifier can be any of the following aliases:</span></span>

- <span data-ttu-id="14e18-106">Alias przestrzeni nazw utworzony za pomocą [dyrektywy aliasu using](../keywords/using-directive.md):</span><span class="sxs-lookup"><span data-stu-id="14e18-106">A namespace alias created with the [using alias directive](../keywords/using-directive.md):</span></span>
  
  ```csharp
  using forwinforms = System.Drawing;
  using forwpf = System.Windows;
  
  public class Converters
  {
      public static forwpf::Point Convert(forwinforms::Point point) => new forwpf::Point(point.X, point.Y);
  }
  ```

- <span data-ttu-id="14e18-107">[Alias zewnętrzny](../keywords/extern-alias.md).</span><span class="sxs-lookup"><span data-stu-id="14e18-107">An [extern alias](../keywords/extern-alias.md).</span></span>
- <span data-ttu-id="14e18-108">`global` Alias, który jest aliasem globalnym przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="14e18-108">The `global` alias, which is the global namespace alias.</span></span> <span data-ttu-id="14e18-109">Globalna przestrzeń nazw jest przestrzenią nazw zawierającą przestrzenie nazw i typy, które nie są zadeklarowane w nazwanym obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="14e18-109">The global namespace is the namespace that contains namespaces and types that are not declared inside a named namespace.</span></span> <span data-ttu-id="14e18-110">Gdy jest używany z `::` kwalifikatorem `global` , alias zawsze odwołuje się do globalnej przestrzeni nazw, nawet jeśli istnieje alias przestrzeni nazw `global` zdefiniowany przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="14e18-110">When used with the `::` qualifier, the `global` alias always references the global namespace, even if there is the user-defined `global` namespace alias.</span></span>
  
  <span data-ttu-id="14e18-111">Poniższy przykład używa `global` aliasu, aby uzyskać dostęp do <xref:System> przestrzeni nazw .NET, która jest elementem członkowskim globalnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="14e18-111">The following example uses the `global` alias to access the .NET <xref:System> namespace, which is a member of the global namespace.</span></span> <span data-ttu-id="14e18-112">Bez aliasu zdefiniowana `System` przez użytkownika przestrzeń nazw, która `MyCompany.MyProduct` jest członkiem przestrzeni nazw, zostanie uzyskany dostęp: `global`</span><span class="sxs-lookup"><span data-stu-id="14e18-112">Without the `global` alias, the user-defined `System` namespace, which is a member of the `MyCompany.MyProduct` namespace, would be accessed:</span></span>

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
  > <span data-ttu-id="14e18-113">Słowo kluczowe jest aliasem globalnym przestrzeni nazw tylko wtedy, gdy jest to identyfikator `::` po lewej stronie kwalifikatora. `global`</span><span class="sxs-lookup"><span data-stu-id="14e18-113">The `global` keyword is the global namespace alias only when it's the left-hand identifier of the `::` qualifier.</span></span>

<span data-ttu-id="14e18-114">Możesz również użyć [operatora `.` dostępu do elementów członkowskich](member-access-operators.md#member-access-operator-) , aby uzyskać dostęp do elementów członkowskich z aliasem.</span><span class="sxs-lookup"><span data-stu-id="14e18-114">You can also use the [member access `.` operator](member-access-operators.md#member-access-operator-) to access members of an aliased namespace.</span></span> <span data-ttu-id="14e18-115">`.` Jednak operator jest również używany do uzyskiwania dostępu do elementów członkowskich typu.</span><span class="sxs-lookup"><span data-stu-id="14e18-115">However, the `.` operator is also used to access members of a type.</span></span> <span data-ttu-id="14e18-116">`::` Kwalifikator gwarantuje, że jego identyfikator po lewej stronie zawsze odwołuje się do aliasu przestrzeni nazw, nawet jeśli istnieje typ lub przestrzeń nazw o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="14e18-116">The `::` qualifier ensures that its left-hand identifier always references a namespace alias, even if there exists a type or namespace with the same name.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="14e18-117">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="14e18-117">C# language specification</span></span>

<span data-ttu-id="14e18-118">Aby uzyskać więcej informacji, zobacz sekcję [kwalifikatory aliasów przestrzeni nazw](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="14e18-118">For more information, see the [Namespace alias qualifiers](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="14e18-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="14e18-119">See also</span></span>

- [<span data-ttu-id="14e18-120">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="14e18-120">C# reference</span></span>](../index.md)
- [<span data-ttu-id="14e18-121">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="14e18-121">C# operators</span></span>](index.md)
- [<span data-ttu-id="14e18-122">Używanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="14e18-122">Using namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
