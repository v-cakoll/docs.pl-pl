---
title: Niebezpieczny kod i wskaźniki - C# przewodnik programowania
ms.custom: seodec18
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
ms.openlocfilehash: 3712e04d4496d13178843564b5d0753f62e28fa0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61678106"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a><span data-ttu-id="aa39f-102">Niebezpieczny kod i wskaźniki (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="aa39f-102">Unsafe Code and Pointers (C# Programming Guide)</span></span>
<span data-ttu-id="aa39f-103">Aby zachować bezpieczeństwo typów i zabezpieczeń, C# nie obsługuje arytmetyki wskaźnika domyślnie.</span><span class="sxs-lookup"><span data-stu-id="aa39f-103">To maintain type safety and security, C# does not support pointer arithmetic, by default.</span></span> <span data-ttu-id="aa39f-104">Jednak przy użyciu [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) słów kluczowych, można zdefiniować niebezpieczny kontekst, w którym można użyć wskaźników.</span><span class="sxs-lookup"><span data-stu-id="aa39f-104">However, by using the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword, you can define an unsafe context in which pointers can be used.</span></span> <span data-ttu-id="aa39f-105">Aby uzyskać więcej informacji o wskaźnikach, zobacz temat [typy wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="aa39f-105">For more information about pointers, see the topic [Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa39f-106">W środowisko uruchomieniowe języka wspólnego (CLR) niebezpieczny kod nazywa się zweryfikowanie kodu.</span><span class="sxs-lookup"><span data-stu-id="aa39f-106">In the common language runtime (CLR), unsafe code is referred to as unverifiable code.</span></span> <span data-ttu-id="aa39f-107">Niebezpieczny kod w języku C# nie są zawsze niebezpieczne; jest po prostu kod bezpieczeństwa, którego nie można zweryfikować przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="aa39f-107">Unsafe code in C# is not necessarily dangerous; it is just code whose safety cannot be verified by the CLR.</span></span> <span data-ttu-id="aa39f-108">Środowisko CLR w związku z tym tylko wykona niebezpieczny kod jeśli znajduje się w zestawie całkowicie zaufanym.</span><span class="sxs-lookup"><span data-stu-id="aa39f-108">The CLR will therefore only execute unsafe code if it is in a fully trusted assembly.</span></span> <span data-ttu-id="aa39f-109">Jeśli używasz niebezpieczny kod, jest odpowiedzialny za zapewnienie, kod nie wprowadzają zagrożenia dla bezpieczeństwa lub wskaźnik błędów.</span><span class="sxs-lookup"><span data-stu-id="aa39f-109">If you use unsafe code, it is your responsibility to ensure that your code does not introduce security risks or pointer errors.</span></span>  
  
## <a name="unsafe-code-overview"></a><span data-ttu-id="aa39f-110">Niebezpieczne przegląd kodu</span><span class="sxs-lookup"><span data-stu-id="aa39f-110">Unsafe Code Overview</span></span>  
 <span data-ttu-id="aa39f-111">Niebezpieczny kod ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="aa39f-111">Unsafe code has the following properties:</span></span>  
  
- <span data-ttu-id="aa39f-112">Metody, typy i bloków kodu mogą być definiowane jako niebezpieczny.</span><span class="sxs-lookup"><span data-stu-id="aa39f-112">Methods, types, and code blocks can be defined as unsafe.</span></span>  
  
- <span data-ttu-id="aa39f-113">W niektórych przypadkach niebezpieczny kod może zwiększyć wydajność aplikacji, usuwając kontroli granice tablicy.</span><span class="sxs-lookup"><span data-stu-id="aa39f-113">In some cases, unsafe code may increase an application's performance by removing array bounds checks.</span></span>  
  
- <span data-ttu-id="aa39f-114">Niebezpieczny kod jest wymagany podczas wywoływania funkcji natywnych, które wymagają wskaźników.</span><span class="sxs-lookup"><span data-stu-id="aa39f-114">Unsafe code is required when you call native functions that require pointers.</span></span>  
  
- <span data-ttu-id="aa39f-115">Za pomocą niebezpieczny kod wprowadza zagrożenia bezpieczeństwa i stabilności.</span><span class="sxs-lookup"><span data-stu-id="aa39f-115">Using unsafe code introduces security and stability risks.</span></span>  
  
- <span data-ttu-id="aa39f-116">W kolejności dla języka C# skompilować kod niebezpieczny, aplikacja musi być skompilowana przy użyciu [/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="aa39f-116">In order for C# to compile unsafe code, the application must be compiled with [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="aa39f-117">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="aa39f-117">Related Sections</span></span>  
 <span data-ttu-id="aa39f-118">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="aa39f-118">For more information, see:</span></span>  
  
- [<span data-ttu-id="aa39f-119">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="aa39f-119">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
- [<span data-ttu-id="aa39f-120">Bufory o ustalonym rozmiarze</span><span class="sxs-lookup"><span data-stu-id="aa39f-120">Fixed Size Buffers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)  
  
- [<span data-ttu-id="aa39f-121">Instrukcje: Użycie wskaźników do kopiowania tablicy bajtów</span><span class="sxs-lookup"><span data-stu-id="aa39f-121">How to: Use Pointers to Copy an Array of Bytes</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/how-to-use-pointers-to-copy-an-array-of-bytes.md)  
  
- [<span data-ttu-id="aa39f-122">unsafe</span><span class="sxs-lookup"><span data-stu-id="aa39f-122">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="aa39f-123">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="aa39f-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="aa39f-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aa39f-124">See also</span></span>

- [<span data-ttu-id="aa39f-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="aa39f-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
