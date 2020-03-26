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
# <a name="-operator-c-reference"></a><span data-ttu-id="f1b3f-102">:: operator (odwołanie C#)</span><span class="sxs-lookup"><span data-stu-id="f1b3f-102">:: operator (C# reference)</span></span>

<span data-ttu-id="f1b3f-103">Użyj kwalifikatora `::` aliasu obszaru nazw, aby uzyskać dostęp do członka aliasowanego obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="f1b3f-103">Use the namespace alias qualifier `::` to access a member of an aliased namespace.</span></span> <span data-ttu-id="f1b3f-104">`::` Kwalifikatora można używać tylko między dwoma identyfikatorami.</span><span class="sxs-lookup"><span data-stu-id="f1b3f-104">You can use the `::` qualifier only between two identifiers.</span></span> <span data-ttu-id="f1b3f-105">Identyfikatorem po lewej stronie może być dowolny z następujących aliasów:</span><span class="sxs-lookup"><span data-stu-id="f1b3f-105">The left-hand identifier can be any of the following aliases:</span></span>

- <span data-ttu-id="f1b3f-106">Alias obszaru nazw utworzony przy [użyciu dyrektywy aliasu:](../keywords/using-directive.md)</span><span class="sxs-lookup"><span data-stu-id="f1b3f-106">A namespace alias created with a [using alias directive](../keywords/using-directive.md):</span></span>

  ```csharp
  using forwinforms = System.Drawing;
  using forwpf = System.Windows;
  
  public class Converters
  {
      public static forwpf::Point Convert(forwinforms::Point point) => new forwpf::Point(point.X, point.Y);
  }
  ```

- <span data-ttu-id="f1b3f-107">Alias [extern](../keywords/extern-alias.md).</span><span class="sxs-lookup"><span data-stu-id="f1b3f-107">An [extern alias](../keywords/extern-alias.md).</span></span>
- <span data-ttu-id="f1b3f-108">Alias, `global` który jest aliasem globalnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f1b3f-108">The `global` alias, which is the global namespace alias.</span></span> <span data-ttu-id="f1b3f-109">Globalna przestrzeń nazw to obszar nazw zawierający obszary nazw i typy, które nie są zadeklarowane w nazwanej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f1b3f-109">The global namespace is the namespace that contains namespaces and types that are not declared inside a named namespace.</span></span> <span data-ttu-id="f1b3f-110">W przypadku `::` użycia z `global` kwalifikatorem alias zawsze odwołuje się do `global` globalnej przestrzeni nazw, nawet jeśli istnieje alias obszaru nazw zdefiniowany przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f1b3f-110">When used with the `::` qualifier, the `global` alias always references the global namespace, even if there is the user-defined `global` namespace alias.</span></span>

  <span data-ttu-id="f1b3f-111">W poniższym przykładzie użyto aliasu, `global` aby uzyskać dostęp do obszaru nazw platformy .NET, <xref:System> który jest członkiem globalnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f1b3f-111">The following example uses the `global` alias to access the .NET <xref:System> namespace, which is a member of the global namespace.</span></span> <span data-ttu-id="f1b3f-112">Bez `global` aliasu dostęp do `System` zdefiniowanego przez użytkownika obszaru `MyCompany.MyProduct` nazw, który jest członkiem obszaru nazw, będzie dostępny:</span><span class="sxs-lookup"><span data-stu-id="f1b3f-112">Without the `global` alias, the user-defined `System` namespace, which is a member of the `MyCompany.MyProduct` namespace, would be accessed:</span></span>

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
  > <span data-ttu-id="f1b3f-113">Słowo `global` kluczowe jest aliasem globalnej przestrzeni nazw tylko wtedy, `::` gdy jest to identyfikator po lewej stronie kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="f1b3f-113">The `global` keyword is the global namespace alias only when it's the left-hand identifier of the `::` qualifier.</span></span>

<span data-ttu-id="f1b3f-114">Token można również [ `.` użyć,](member-access-operators.md#member-access-expression-) aby uzyskać dostęp do członka obszaru nazw o aliasie.</span><span class="sxs-lookup"><span data-stu-id="f1b3f-114">You can also use the [`.` token](member-access-operators.md#member-access-expression-) to access a member of an aliased namespace.</span></span> <span data-ttu-id="f1b3f-115">Jednak `.` token jest również używany do dostępu do elementu członkowskiego typu.</span><span class="sxs-lookup"><span data-stu-id="f1b3f-115">However, the `.` token is also used to access a type member.</span></span> <span data-ttu-id="f1b3f-116">Kwalifikator `::` zapewnia, że jego identyfikator po lewej stronie zawsze odwołuje się do aliasu obszaru nazw, nawet jeśli istnieje typ lub obszar nazw o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="f1b3f-116">The `::` qualifier ensures that its left-hand identifier always references a namespace alias, even if there exists a type or namespace with the same name.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f1b3f-117">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f1b3f-117">C# language specification</span></span>

<span data-ttu-id="f1b3f-118">Aby uzyskać więcej informacji, zobacz sekcję [Kwalifikatory aliasów obszaru nazw](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) [w specyfikacji języka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="f1b3f-118">For more information, see the [Namespace alias qualifiers](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f1b3f-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f1b3f-119">See also</span></span>

- [<span data-ttu-id="f1b3f-120">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f1b3f-120">C# reference</span></span>](../index.md)
- [<span data-ttu-id="f1b3f-121">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="f1b3f-121">C# operators</span></span>](index.md)
- [<span data-ttu-id="f1b3f-122">Korzystanie z obszarów nazw</span><span class="sxs-lookup"><span data-stu-id="f1b3f-122">Using namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
