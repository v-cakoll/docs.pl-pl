---
title: . Operator - C# odwołania
ms.custom: seodec18
ms.date: 02/25/2019
f1_keywords:
- ._CSharpKeyword
helpviewer_keywords:
- member access operator (.) [C#]
- . operator [C#]
- dot operator (.) [C#]
ms.assetid: a1f54b52-b686-4ae5-a48e-a2a9ebd0eb7b
ms.openlocfilehash: 2661676d53deb874c5e5a90b4443b301730e09df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61689206"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="06e76-103">.</span><span class="sxs-lookup"><span data-stu-id="06e76-103">.</span></span> <span data-ttu-id="06e76-104">operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="06e76-104">operator (C# Reference)</span></span>

<span data-ttu-id="06e76-105">Kropki (.), `.`, jest zwykle używany podczas dostępu do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="06e76-105">The dot, `.`, is typically used for member access.</span></span>

<span data-ttu-id="06e76-106">Możesz użyć `.` token w celu uzyskania dostępu do członka przestrzeni nazw lub typ, jak w poniższych przykładach pokazano:</span><span class="sxs-lookup"><span data-stu-id="06e76-106">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="06e76-107">Użyj `.` dostępu zagnieżdżone przestrzenie nazw w przestrzeni nazw, w poniższym przykładzie z do [ `using` dyrektywy](../keywords/using-directive.md) pokazuje:</span><span class="sxs-lookup"><span data-stu-id="06e76-107">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](~/samples/snippets/csharp/language-reference/operators/MemberAccessExamples.cs#NestedNamespace)]

- <span data-ttu-id="06e76-108">Użyj `.` do formularza *kwalifikowana nazwa* uzyskiwać dostęp do typu, w przestrzeni nazw, co ilustruje poniższy kod:</span><span class="sxs-lookup"><span data-stu-id="06e76-108">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](~/samples/snippets/csharp/language-reference/operators/MemberAccessExamples.cs#QualifiedName)]

  <span data-ttu-id="06e76-109">Użyj [ `using` dyrektywy](../keywords/using-directive.md) powoduje użycie kwalifikowane nazwy są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="06e76-109">Use the [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="06e76-110">Użyj `.` dostęp do [elementy członkowskie typu](../../programming-guide/classes-and-structs/index.md#members)statycznych i niestatycznych, co ilustruje poniższy kod:</span><span class="sxs-lookup"><span data-stu-id="06e76-110">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](~/samples/snippets/csharp/language-reference/operators/MemberAccessExamples.cs#TypeMemberAccess)]

<span data-ttu-id="06e76-111">Można również użyć `.` do wywołania [— metoda rozszerzenia](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="06e76-111">You can also use `.` to invoke an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="06e76-112">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="06e76-112">Operator overloadability</span></span>

<span data-ttu-id="06e76-113">Operator `.` nie mogą być przeciążone.</span><span class="sxs-lookup"><span data-stu-id="06e76-113">The operator `.` cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="06e76-114">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="06e76-114">C# language specification</span></span>

<span data-ttu-id="06e76-115">Aby uzyskać więcej informacji, zobacz [dostęp do elementu członkowskiego](~/_csharplang/spec/expressions.md#member-access) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="06e76-115">For more information, see the [Member access](~/_csharplang/spec/expressions.md#member-access) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="06e76-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06e76-116">See also</span></span>

- [<span data-ttu-id="06e76-117">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="06e76-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="06e76-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="06e76-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="06e76-119">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="06e76-119">C# Operators</span></span>](index.md)
- <span data-ttu-id="06e76-120">[?. i? Operatory]](null-conditional-operators.md)</span><span class="sxs-lookup"><span data-stu-id="06e76-120">[?. and ?[] operators](null-conditional-operators.md)</span></span>