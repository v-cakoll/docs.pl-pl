---
title: Ograniczniki tagów dokumentacji — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
ms.openlocfilehash: 064519e6d849736690f28c78e0efbc4067f9e6a9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711795"
---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a><span data-ttu-id="706de-102">Ograniczniki znaczników dokumentacji (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="706de-102">Delimiters for Documentation Tags (C# Programming Guide)</span></span>
<span data-ttu-id="706de-103">Użycie komentarzy w dokumencie XML wymaga ograniczników wskazujących kompilatorowi, w którym rozpoczyna się i kończą komentarz dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="706de-103">The use of XML doc comments requires delimiters, which indicate to the compiler where a documentation comment begins and ends.</span></span> <span data-ttu-id="706de-104">Do tagów dokumentacji XML można używać następujących rodzajów ograniczników:</span><span class="sxs-lookup"><span data-stu-id="706de-104">You can use the following kinds of delimiters with the XML documentation tags:</span></span>  
  
 `///`  
 <span data-ttu-id="706de-105">Ogranicznik pojedynczej linii.</span><span class="sxs-lookup"><span data-stu-id="706de-105">Single-line delimiter.</span></span> <span data-ttu-id="706de-106">Jest to formularz, który jest wyświetlany w przykładach dokumentacji i używany przez szablony C# projektu wizualnego.</span><span class="sxs-lookup"><span data-stu-id="706de-106">This is the form that is shown in documentation examples and used by the Visual C# project templates.</span></span> <span data-ttu-id="706de-107">Jeśli występuje znak spacji po ograniczniku, ten znak nie jest uwzględniany w danych wyjściowych XML.</span><span class="sxs-lookup"><span data-stu-id="706de-107">If there is a white space character following the delimiter, that character is not included in the XML output.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="706de-108">Środowisko IDE programu Visual Studio ma funkcję o nazwie edytowanie komentarzy inteligentnych, która automatycznie wstawia > podsumowania \<i \</Summary > Tagi i przenosi kursor w tych tagach po wpisaniu ogranicznika `///` w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="706de-108">The Visual Studio IDE has a feature called Smart Comment Editing that automatically inserts the \<summary> and \</summary> tags and moves your cursor within these tags after you type the `///` delimiter in the Code Editor.</span></span> <span data-ttu-id="706de-109">Tę funkcję można włączać lub wyłączać w [oknie dialogowym Opcje](/visualstudio/ide/reference/options-text-editor-csharp-advanced).</span><span class="sxs-lookup"><span data-stu-id="706de-109">You can turn this feature on or off in the [Options dialog box](/visualstudio/ide/reference/options-text-editor-csharp-advanced).</span></span>  
  
 `/** */`  
 <span data-ttu-id="706de-110">Ograniczniki wielowierszowe.</span><span class="sxs-lookup"><span data-stu-id="706de-110">Multiline delimiters.</span></span>  
  
 <span data-ttu-id="706de-111">Istnieją pewne reguły formatowania, które należy stosować w przypadku używania ograniczników `/** */`.</span><span class="sxs-lookup"><span data-stu-id="706de-111">There are some formatting rules to follow when you use the `/** */` delimiters.</span></span>  
  
- <span data-ttu-id="706de-112">W wierszu zawierającym ogranicznik `/**`, jeśli pozostała część wiersza jest białym znakiem, wiersz nie jest przetwarzany dla komentarzy.</span><span class="sxs-lookup"><span data-stu-id="706de-112">On the line that contains the `/**` delimiter, if the remainder of the line is white space, the line is not processed for comments.</span></span> <span data-ttu-id="706de-113">Jeśli pierwszy znak po ograniczniku `/**` jest białym znakiem, oznacza to, że odstęp jest ignorowany, a pozostała część wiersza jest przetwarzana.</span><span class="sxs-lookup"><span data-stu-id="706de-113">If the first character after the `/**` delimiter is white space, that white space character is ignored and the rest of the line is processed.</span></span> <span data-ttu-id="706de-114">W przeciwnym razie cały tekst wiersza po przekroczeniu ogranicznika `/**` jest przetwarzany jako część komentarza.</span><span class="sxs-lookup"><span data-stu-id="706de-114">Otherwise, the entire text of the line after the `/**` delimiter is processed as part of the comment.</span></span>  
  
- <span data-ttu-id="706de-115">W wierszu zawierającym ogranicznik `*/`, jeśli występuje tylko białe miejsce do ogranicznika `*/`, ten wiersz jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="706de-115">On the line that contains the `*/` delimiter, if there is only white space up to the `*/` delimiter, that line is ignored.</span></span> <span data-ttu-id="706de-116">W przeciwnym razie tekst w wierszu do ogranicznika `*/` jest przetwarzany jako część komentarza, zgodnie z regułami dopasowywania wzorców opisanymi w następującym punkcie.</span><span class="sxs-lookup"><span data-stu-id="706de-116">Otherwise, the text on the line up to the `*/` delimiter is processed as part of the comment, subject to the pattern-matching rules described in the following bullet.</span></span>  
  
- <span data-ttu-id="706de-117">Dla linii po tej, która rozpoczyna się od ogranicznika `/**`, kompilator szuka wspólnego wzorca na początku każdego wiersza.</span><span class="sxs-lookup"><span data-stu-id="706de-117">For the lines after the one that begins with the `/**` delimiter, the compiler looks for a common pattern at the beginning of each line.</span></span> <span data-ttu-id="706de-118">Wzorzec może składać się z opcjonalnego odstępu i gwiazdki (`*`), po którym następuje bardziej opcjonalny odstęp.</span><span class="sxs-lookup"><span data-stu-id="706de-118">The pattern can consist of optional white space and an asterisk (`*`), followed by more optional white space.</span></span> <span data-ttu-id="706de-119">Jeśli kompilator odnajdzie wspólny wzorzec na początku każdego wiersza, który nie zaczyna się od ogranicznika `/**` lub ogranicznika `*/`, zignoruje ten wzorzec dla każdego wiersza.</span><span class="sxs-lookup"><span data-stu-id="706de-119">If the compiler finds a common pattern at the beginning of each line that does not begin with the `/**` delimiter or the `*/` delimiter, it ignores that pattern for each line.</span></span>  
  
 <span data-ttu-id="706de-120">Poniższe przykłady ilustrują te reguły.</span><span class="sxs-lookup"><span data-stu-id="706de-120">The following examples illustrate these rules.</span></span>  
  
- <span data-ttu-id="706de-121">Jedyną częścią poniższego komentarza, który zostanie przetworzony, jest wiersz zaczynający się od `<summary>`.</span><span class="sxs-lookup"><span data-stu-id="706de-121">The only part of the following comment that will be processed is the line that begins with `<summary>`.</span></span> <span data-ttu-id="706de-122">Trzy formaty tagów dają te same Komentarze.</span><span class="sxs-lookup"><span data-stu-id="706de-122">The three tag formats produce the same comments.</span></span>  
  
    ```csharp  
    /** <summary>text</summary> */   
  
    /**   
    <summary>text</summary>   
    */   
  
    /**   
     * <summary>text</summary>   
    */  
    ```  
  
- <span data-ttu-id="706de-123">Kompilator identyfikuje wspólny wzorzec "\*" na początku drugiego i trzeciego wiersza.</span><span class="sxs-lookup"><span data-stu-id="706de-123">The compiler identifies a common pattern of " \* " at the beginning of the second and third lines.</span></span> <span data-ttu-id="706de-124">Wzorzec nie jest uwzględniony w danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="706de-124">The pattern is not included in the output.</span></span>  
  
    ```csharp  
    /**   
     * <summary>   
     * text </summary>*/   
    ```  
  
- <span data-ttu-id="706de-125">Kompilator nie znalazł wspólnego wzorca w poniższym komentarzu, ponieważ drugi znak w trzecim wierszu nie jest gwiazdką.</span><span class="sxs-lookup"><span data-stu-id="706de-125">The compiler finds no common pattern in the following comment because the second character on the third line is not an asterisk.</span></span> <span data-ttu-id="706de-126">W związku z tym cały tekst w drugim i trzecim wierszu jest przetwarzany w ramach komentarza.</span><span class="sxs-lookup"><span data-stu-id="706de-126">Therefore, all text on the second and third lines is processed as part of the comment.</span></span>  
  
    ```csharp  
    /**   
     * <summary>   
       text </summary>  
    */   
    ```  
  
- <span data-ttu-id="706de-127">Kompilator nie znalazł wzorca w poniższym komentarzu z dwóch przyczyn.</span><span class="sxs-lookup"><span data-stu-id="706de-127">The compiler finds no pattern in the following comment for two reasons.</span></span> <span data-ttu-id="706de-128">Najpierw liczba spacji przed gwiazdką nie jest spójna.</span><span class="sxs-lookup"><span data-stu-id="706de-128">First, the number of spaces before the asterisk is not consistent.</span></span> <span data-ttu-id="706de-129">Sekunda, piąta linia zaczyna się od karty, która nie jest zgodna z spacjami.</span><span class="sxs-lookup"><span data-stu-id="706de-129">Second, the fifth line begins with a tab, which does not match spaces.</span></span> <span data-ttu-id="706de-130">W związku z tym cały tekst z wierszy od dwóch do pięciu jest przetwarzany jako część komentarza.</span><span class="sxs-lookup"><span data-stu-id="706de-130">Therefore, all text from lines two through five is processed as part of the comment.</span></span>  
  
    ```csharp  
    /**   
      * <summary>   
      * text   
     *  text2   
        *  </summary>   
    */   
    ```  
  
## <a name="see-also"></a><span data-ttu-id="706de-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="706de-131">See also</span></span>

- [<span data-ttu-id="706de-132">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="706de-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="706de-133">Komentarze dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="706de-133">XML Documentation Comments</span></span>](./index.md)
- [<span data-ttu-id="706de-134">-doc (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="706de-134">-doc (C# Compiler Options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="706de-135">Komentarze dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="706de-135">XML Documentation Comments</span></span>](./index.md)
