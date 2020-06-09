---
title: Ograniczniki tagów dokumentacji — Przewodnik programowania w języku C#
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
ms.openlocfilehash: db8d43edc8b7cb0066fd3afcb75a1852603e86c4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594429"
---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a><span data-ttu-id="90128-102">Ograniczniki tagów dokumentacji (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="90128-102">Delimiters for documentation tags (C# programming guide)</span></span>

<span data-ttu-id="90128-103">Użycie komentarzy w dokumencie XML wymaga ograniczników wskazujących kompilatorowi, w którym rozpoczyna się i kończą komentarz dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="90128-103">The use of XML doc comments requires delimiters, which indicate to the compiler where a documentation comment begins and ends.</span></span> <span data-ttu-id="90128-104">Do tagów dokumentacji XML można używać następujących rodzajów ograniczników:</span><span class="sxs-lookup"><span data-stu-id="90128-104">You can use the following kinds of delimiters with the XML documentation tags:</span></span>

- `///`

  <span data-ttu-id="90128-105">Ogranicznik pojedynczej linii.</span><span class="sxs-lookup"><span data-stu-id="90128-105">Single-line delimiter.</span></span> <span data-ttu-id="90128-106">Jest to formularz, który jest wyświetlany w przykładach dokumentacji i używany przez szablony projektu C#.</span><span class="sxs-lookup"><span data-stu-id="90128-106">This is the form that is shown in documentation examples and used by the C# project templates.</span></span> <span data-ttu-id="90128-107">Jeśli występuje znak spacji po ograniczniku, ten znak nie jest uwzględniany w danych wyjściowych XML.</span><span class="sxs-lookup"><span data-stu-id="90128-107">If there is a white space character following the delimiter, that character is not included in the XML output.</span></span>

  > [!NOTE]
  > <span data-ttu-id="90128-108">Zintegrowane środowisko programistyczne (IDE) programu Visual Studio automatycznie wstawia `<summary>` `</summary>` Tagi i i przenosi kursor w tych tagach po wpisaniu `///` ogranicznika w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="90128-108">The Visual Studio integrated development environment (IDE) automatically inserts the `<summary>` and `</summary>` tags and moves your cursor within these tags after you type the `///` delimiter in the code editor.</span></span> <span data-ttu-id="90128-109">Tę funkcję można włączać lub wyłączać w [oknie dialogowym Opcje](/visualstudio/ide/reference/options-text-editor-csharp-advanced).</span><span class="sxs-lookup"><span data-stu-id="90128-109">You can turn this feature on or off in the [Options dialog box](/visualstudio/ide/reference/options-text-editor-csharp-advanced).</span></span>
  
- `/** */`

  <span data-ttu-id="90128-110">Ograniczniki wielowierszowe.</span><span class="sxs-lookup"><span data-stu-id="90128-110">Multiline delimiters.</span></span>

  <span data-ttu-id="90128-111">Podczas używania ograniczników obowiązują pewne reguły formatowania `/** */` :</span><span class="sxs-lookup"><span data-stu-id="90128-111">There are some formatting rules to follow when you use the `/** */` delimiters:</span></span>
  
  - <span data-ttu-id="90128-112">W wierszu zawierającym `/**` ogranicznik, jeśli pozostała część wiersza jest białym znakiem, wiersz nie jest przetwarzany dla komentarzy.</span><span class="sxs-lookup"><span data-stu-id="90128-112">On the line that contains the `/**` delimiter, if the remainder of the line is white space, the line is not processed for comments.</span></span> <span data-ttu-id="90128-113">Jeśli pierwszy znak po `/**` ograniczniku jest znakiem odstępu, oznacza to, że biały znak jest ignorowany, a reszta wiersza jest przetwarzana.</span><span class="sxs-lookup"><span data-stu-id="90128-113">If the first character after the `/**` delimiter is white space, that white space character is ignored and the rest of the line is processed.</span></span> <span data-ttu-id="90128-114">W przeciwnym razie cały tekst wiersza po `/**` ograniczniku zostanie przetworzony jako część komentarza.</span><span class="sxs-lookup"><span data-stu-id="90128-114">Otherwise, the entire text of the line after the `/**` delimiter is processed as part of the comment.</span></span>

  - <span data-ttu-id="90128-115">W wierszu zawierającym `*/` ogranicznik, jeśli występuje tylko biały znak do `*/` ogranicznika, ten wiersz jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="90128-115">On the line that contains the `*/` delimiter, if there is only white space up to the `*/` delimiter, that line is ignored.</span></span> <span data-ttu-id="90128-116">W przeciwnym razie tekst w wierszu do `*/` ogranicznika jest przetwarzany jako część komentarza.</span><span class="sxs-lookup"><span data-stu-id="90128-116">Otherwise, the text on the line up to the `*/` delimiter is processed as part of the comment.</span></span>
  
  - <span data-ttu-id="90128-117">Dla wierszy po tym, które zaczyna się od `/**` ogranicznika, kompilator szuka wspólnego wzorca na początku każdego wiersza.</span><span class="sxs-lookup"><span data-stu-id="90128-117">For the lines after the one that begins with the `/**` delimiter, the compiler looks for a common pattern at the beginning of each line.</span></span> <span data-ttu-id="90128-118">Wzorzec może składać się z opcjonalnego odstępu i gwiazdki ( `*` ), po którym następuje bardziej opcjonalny odstęp.</span><span class="sxs-lookup"><span data-stu-id="90128-118">The pattern can consist of optional white space and an asterisk (`*`), followed by more optional white space.</span></span> <span data-ttu-id="90128-119">Jeśli kompilator odnajdzie wspólny wzorzec na początku każdego wiersza, który nie zaczyna się od `/**` ogranicznika lub `*/` ogranicznika, ignoruje ten wzorzec dla każdego wiersza.</span><span class="sxs-lookup"><span data-stu-id="90128-119">If the compiler finds a common pattern at the beginning of each line that does not begin with the `/**` delimiter or the `*/` delimiter, it ignores that pattern for each line.</span></span>

  <span data-ttu-id="90128-120">Poniższe przykłady ilustrują te reguły.</span><span class="sxs-lookup"><span data-stu-id="90128-120">The following examples illustrate these rules.</span></span>

  - <span data-ttu-id="90128-121">Jedyną częścią poniższego komentarza, który jest przetwarzany, jest wiersz zaczynający się od `<summary>` .</span><span class="sxs-lookup"><span data-stu-id="90128-121">The only part of the following comment that's processed is the line that begins with `<summary>`.</span></span> <span data-ttu-id="90128-122">Trzy formaty tagów dają te same Komentarze.</span><span class="sxs-lookup"><span data-stu-id="90128-122">The three tag formats produce the same comments.</span></span>

    ```csharp
    /** <summary>text</summary> */

    /**
    <summary>text</summary>
    */

    /**
     * <summary>text</summary>
    */
    ```

  - <span data-ttu-id="90128-123">Kompilator identyfikuje wspólny wzorzec " \* " na początku drugiego i trzeciego wiersza.</span><span class="sxs-lookup"><span data-stu-id="90128-123">The compiler identifies a common pattern of " \* " at the beginning of the second and third lines.</span></span> <span data-ttu-id="90128-124">Wzorzec nie jest uwzględniony w danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="90128-124">The pattern is not included in the output.</span></span>

    ```csharp
    /**
     * <summary>
     * text </summary>*/
    ```

  - <span data-ttu-id="90128-125">Kompilator nie znalazł wspólnego wzorca w poniższym komentarzu, ponieważ drugi znak w trzecim wierszu nie jest gwiazdką.</span><span class="sxs-lookup"><span data-stu-id="90128-125">The compiler finds no common pattern in the following comment because the second character on the third line is not an asterisk.</span></span> <span data-ttu-id="90128-126">W związku z tym cały tekst w drugim i trzecim wierszu jest przetwarzany w ramach komentarza.</span><span class="sxs-lookup"><span data-stu-id="90128-126">Therefore, all text on the second and third lines is processed as part of the comment.</span></span>

    ```csharp
    /**
     * <summary>
       text </summary>
    */
    ```

  - <span data-ttu-id="90128-127">Kompilator nie znalazł wzorca w poniższym komentarzu z dwóch przyczyn.</span><span class="sxs-lookup"><span data-stu-id="90128-127">The compiler finds no pattern in the following comment for two reasons.</span></span> <span data-ttu-id="90128-128">Najpierw liczba spacji przed gwiazdką nie jest spójna.</span><span class="sxs-lookup"><span data-stu-id="90128-128">First, the number of spaces before the asterisk is not consistent.</span></span> <span data-ttu-id="90128-129">Sekunda, piąta linia zaczyna się od karty, która nie jest zgodna z spacjami.</span><span class="sxs-lookup"><span data-stu-id="90128-129">Second, the fifth line begins with a tab, which does not match spaces.</span></span> <span data-ttu-id="90128-130">W związku z tym cały tekst z wierszy od dwóch do pięciu jest przetwarzany jako część komentarza.</span><span class="sxs-lookup"><span data-stu-id="90128-130">Therefore, all text from lines two through five is processed as part of the comment.</span></span>

    <!-- markdownlint-disable MD010 -->
    ```csharp
    /**
      * <summary>
      * text
     *  text2
        *  </summary>
    */
    ```
    <!-- markdownlint-enable MD010 -->

## <a name="see-also"></a><span data-ttu-id="90128-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="90128-131">See also</span></span>

- [<span data-ttu-id="90128-132">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="90128-132">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="90128-133">Komentarze dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="90128-133">XML documentation comments</span></span>](./index.md)
- [<span data-ttu-id="90128-134">-doc (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="90128-134">-doc (C# compiler options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
