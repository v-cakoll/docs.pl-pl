---
title: Niebezpieczny kod i wskaźniki — przewodnik programowania języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- security [C#], type safety
- C# language, unsafe code
- type safety [C#]
- unsafe keyword [C#]
- unsafe code [C#]
- C# language, pointers
- pointers [C#], about pointers
ms.assetid: b0fcca10-a92d-4f2a-835b-b0ccae6739ee
ms.openlocfilehash: 013af4e55c8fc396bbc92058d7fb454484f3263e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711834"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a><span data-ttu-id="48b1f-102">Niebezpieczny kod i wskaźniki (Przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="48b1f-102">Unsafe code and pointers (C# Programming Guide)</span></span>

<span data-ttu-id="48b1f-103">Aby zachować bezpieczeństwo typów i zabezpieczeń, C# nie obsługuje wskaźnik arytmetyczny, domyślnie.</span><span class="sxs-lookup"><span data-stu-id="48b1f-103">To maintain type safety and security, C# does not support pointer arithmetic, by default.</span></span> <span data-ttu-id="48b1f-104">Jednak za pomocą [niebezpiecznego](../../language-reference/keywords/unsafe.md) słowa kluczowego można zdefiniować niebezpieczny kontekst, w którym można używać wskaźników.</span><span class="sxs-lookup"><span data-stu-id="48b1f-104">However, by using the [unsafe](../../language-reference/keywords/unsafe.md) keyword, you can define an unsafe context in which pointers can be used.</span></span> <span data-ttu-id="48b1f-105">Aby uzyskać więcej informacji o wskaźnikach, zobacz [Typy wskaźników](pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="48b1f-105">For more information about pointers, see [Pointer types](pointer-types.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="48b1f-106">W czasie wykonywania języka wspólnego (CLR) niebezpieczny kod jest określany jako kod nieweryfikowalny.</span><span class="sxs-lookup"><span data-stu-id="48b1f-106">In the common language runtime (CLR), unsafe code is referred to as unverifiable code.</span></span> <span data-ttu-id="48b1f-107">Niebezpieczny kod w języku C# niekoniecznie jest niebezpieczne; jest to tylko kod, którego bezpieczeństwo nie może być zweryfikowane przez CLR.</span><span class="sxs-lookup"><span data-stu-id="48b1f-107">Unsafe code in C# is not necessarily dangerous; it is just code whose safety cannot be verified by the CLR.</span></span> <span data-ttu-id="48b1f-108">W związku z tym clr będzie wykonywać niebezpieczny kod tylko wtedy, gdy znajduje się w pełni zaufanym zestawie.</span><span class="sxs-lookup"><span data-stu-id="48b1f-108">The CLR will therefore only execute unsafe code if it is in a fully trusted assembly.</span></span> <span data-ttu-id="48b1f-109">Jeśli używasz niebezpiecznego kodu, to jest twoim obowiązkiem, aby upewnić się, że kod nie wprowadza zagrożenia bezpieczeństwa lub błędy wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="48b1f-109">If you use unsafe code, it is your responsibility to ensure that your code does not introduce security risks or pointer errors.</span></span>  
  
## <a name="unsafe-code-overview"></a><span data-ttu-id="48b1f-110">Omówienie niebezpiecznego kodu</span><span class="sxs-lookup"><span data-stu-id="48b1f-110">Unsafe code overview</span></span>

<span data-ttu-id="48b1f-111">Niebezpieczny kod ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="48b1f-111">Unsafe code has the following properties:</span></span>

- <span data-ttu-id="48b1f-112">Metody, typy i bloki kodu można zdefiniować jako niebezpieczne.</span><span class="sxs-lookup"><span data-stu-id="48b1f-112">Methods, types, and code blocks can be defined as unsafe.</span></span>

- <span data-ttu-id="48b1f-113">W niektórych przypadkach niebezpieczny kod może zwiększyć wydajność aplikacji, usuwając kontrole granic tablicy.</span><span class="sxs-lookup"><span data-stu-id="48b1f-113">In some cases, unsafe code may increase an application's performance by removing array bounds checks.</span></span>

- <span data-ttu-id="48b1f-114">Niebezpieczny kod jest wymagany podczas wywoływania funkcji macierzystych, które wymagają wskaźników.</span><span class="sxs-lookup"><span data-stu-id="48b1f-114">Unsafe code is required when you call native functions that require pointers.</span></span>

- <span data-ttu-id="48b1f-115">Używanie niebezpiecznego kodu wprowadza zagrożenia bezpieczeństwa i stabilności.</span><span class="sxs-lookup"><span data-stu-id="48b1f-115">Using unsafe code introduces security and stability risks.</span></span>

- <span data-ttu-id="48b1f-116">Kod, który zawiera niebezpieczne bloki muszą być skompilowane z [opcją kompilatora -niebezpieczne.](../../language-reference/compiler-options/unsafe-compiler-option.md)</span><span class="sxs-lookup"><span data-stu-id="48b1f-116">The code that contains unsafe blocks must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="48b1f-117">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="48b1f-117">Related sections</span></span>

<span data-ttu-id="48b1f-118">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="48b1f-118">For more information, see:</span></span>

- [<span data-ttu-id="48b1f-119">Typy wskaźnika</span><span class="sxs-lookup"><span data-stu-id="48b1f-119">Pointer types</span></span>](pointer-types.md)

- [<span data-ttu-id="48b1f-120">Bufory o ustalonym rozmiarze</span><span class="sxs-lookup"><span data-stu-id="48b1f-120">Fixed size buffers</span></span>](fixed-size-buffers.md)

## <a name="c-language-specification"></a><span data-ttu-id="48b1f-121">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="48b1f-121">C# language specification</span></span>

<span data-ttu-id="48b1f-122">Aby uzyskać więcej informacji, zobacz temat [Niebezpieczny kod](~/_csharplang/spec/unsafe-code.md) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="48b1f-122">For more information, see the [Unsafe code](~/_csharplang/spec/unsafe-code.md) topic of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="48b1f-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="48b1f-123">See also</span></span>

- [<span data-ttu-id="48b1f-124">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="48b1f-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="48b1f-125">unsafe</span><span class="sxs-lookup"><span data-stu-id="48b1f-125">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
