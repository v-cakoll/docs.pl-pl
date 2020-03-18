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
# <a name="-operator-c-reference"></a><span data-ttu-id="9f0d3-102">:: operator (odwołanie do Języka C#)</span><span class="sxs-lookup"><span data-stu-id="9f0d3-102">:: operator (C# reference)</span></span>

<span data-ttu-id="9f0d3-103">Użyj kwalifikatora `::` aliasu obszaru nazw, aby uzyskać dostęp do członka aliased namespace.</span><span class="sxs-lookup"><span data-stu-id="9f0d3-103">Use the namespace alias qualifier `::` to access a member of an aliased namespace.</span></span> <span data-ttu-id="9f0d3-104">Kwalifikatora `::` można używać tylko między dwoma identyfikatorami.</span><span class="sxs-lookup"><span data-stu-id="9f0d3-104">You can use the `::` qualifier only between two identifiers.</span></span> <span data-ttu-id="9f0d3-105">Identyfikator po lewej stronie może być dowolny z następujących aliasów:</span><span class="sxs-lookup"><span data-stu-id="9f0d3-105">The left-hand identifier can be any of the following aliases:</span></span>

- <span data-ttu-id="9f0d3-106">Alias obszaru nazw utworzony przy [użyciu aliasdyrektywy:](../keywords/using-directive.md)</span><span class="sxs-lookup"><span data-stu-id="9f0d3-106">A namespace alias created with a [using alias directive](../keywords/using-directive.md):</span></span>

  ```csharp
  using forwinforms = System.Drawing;
  using forwpf = System.Windows;
  
  public class Converters
  {
      public static forwpf::Point Convert(forwinforms::Point point) => new forwpf::Point(point.X, point.Y);
  }
  ```

- <span data-ttu-id="9f0d3-107">Alias [extern](../keywords/extern-alias.md).</span><span class="sxs-lookup"><span data-stu-id="9f0d3-107">An [extern alias](../keywords/extern-alias.md).</span></span>
- <span data-ttu-id="9f0d3-108">Alias, `global` który jest aliasem globalnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="9f0d3-108">The `global` alias, which is the global namespace alias.</span></span> <span data-ttu-id="9f0d3-109">Globalny obszar nazw to obszar nazw zawierający obszary nazw i typy, które nie są zadeklarowane wewnątrz nazwanego obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="9f0d3-109">The global namespace is the namespace that contains namespaces and types that are not declared inside a named namespace.</span></span> <span data-ttu-id="9f0d3-110">W przypadku `::` użycia z `global` kwalifikatorem alias zawsze odwołuje się do `global` globalnego obszaru nazw, nawet jeśli istnieje alias obszaru nazw zdefiniowany przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9f0d3-110">When used with the `::` qualifier, the `global` alias always references the global namespace, even if there is the user-defined `global` namespace alias.</span></span>

  <span data-ttu-id="9f0d3-111">W poniższym `global` przykładzie użyto aliasu, aby uzyskać dostęp do obszaru nazw .NET, <xref:System> który jest członkiem globalnego obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="9f0d3-111">The following example uses the `global` alias to access the .NET <xref:System> namespace, which is a member of the global namespace.</span></span> <span data-ttu-id="9f0d3-112">Bez `global` aliasu można uzyskać `System` dostęp do obszaru nazw zdefiniowanego przez użytkownika, który jest członkiem obszaru `MyCompany.MyProduct` nazw:</span><span class="sxs-lookup"><span data-stu-id="9f0d3-112">Without the `global` alias, the user-defined `System` namespace, which is a member of the `MyCompany.MyProduct` namespace, would be accessed:</span></span>

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
  > <span data-ttu-id="9f0d3-113">Słowo `global` kluczowe jest aliasem globalnej przestrzeni nazw tylko wtedy, `::` gdy jest to lewy identyfikator kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="9f0d3-113">The `global` keyword is the global namespace alias only when it's the left-hand identifier of the `::` qualifier.</span></span>

<span data-ttu-id="9f0d3-114">Można również użyć [operatora `.` dostępu do elementu członkowskiego,](member-access-operators.md#member-access-operator-) aby uzyskać dostęp do elementu członkowskiego aliased obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="9f0d3-114">You can also use the [member access `.` operator](member-access-operators.md#member-access-operator-) to access a member of an aliased namespace.</span></span> <span data-ttu-id="9f0d3-115">Jednak `.` operator jest również używany do uzyskiwania dostępu do elementu członkowskiego typu.</span><span class="sxs-lookup"><span data-stu-id="9f0d3-115">However, the `.` operator is also used to access a type member.</span></span> <span data-ttu-id="9f0d3-116">Kwalifikator `::` zapewnia, że jego lewy identyfikator zawsze odwołuje się do aliasu obszaru nazw, nawet jeśli istnieje typ lub obszar nazw o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="9f0d3-116">The `::` qualifier ensures that its left-hand identifier always references a namespace alias, even if there exists a type or namespace with the same name.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9f0d3-117">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9f0d3-117">C# language specification</span></span>

<span data-ttu-id="9f0d3-118">Aby uzyskać więcej informacji, zobacz sekcję [Kwalifikatory aliasu obszaru nazw](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="9f0d3-118">For more information, see the [Namespace alias qualifiers](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9f0d3-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9f0d3-119">See also</span></span>

- [<span data-ttu-id="9f0d3-120">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9f0d3-120">C# reference</span></span>](../index.md)
- [<span data-ttu-id="9f0d3-121">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="9f0d3-121">C# operators</span></span>](index.md)
- [<span data-ttu-id="9f0d3-122">Korzystanie z przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="9f0d3-122">Using namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
