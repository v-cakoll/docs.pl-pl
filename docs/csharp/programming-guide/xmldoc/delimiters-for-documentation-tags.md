---
title: Ograniczniki dla tagów dokumentacji - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
ms.openlocfilehash: dd4ddb3b324bd6d235efb541c90875dbe9ed4c2d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789832"
---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a><span data-ttu-id="339e0-102">Ograniczniki dla tagów dokumentacji (przewodnik programowania Języka C#)</span><span class="sxs-lookup"><span data-stu-id="339e0-102">Delimiters for documentation tags (C# programming guide)</span></span>

<span data-ttu-id="339e0-103">Korzystanie z komentarzy doc XML wymaga ograniczników, które wskazują do kompilatora, gdzie komentarz dokumentacji zaczyna się i kończy.</span><span class="sxs-lookup"><span data-stu-id="339e0-103">The use of XML doc comments requires delimiters, which indicate to the compiler where a documentation comment begins and ends.</span></span> <span data-ttu-id="339e0-104">Znaczników dokumentacji XML można używać następujących rodzajów ograniczników:</span><span class="sxs-lookup"><span data-stu-id="339e0-104">You can use the following kinds of delimiters with the XML documentation tags:</span></span>

- `///`

  <span data-ttu-id="339e0-105">Ogranicznik jednoliniowy.</span><span class="sxs-lookup"><span data-stu-id="339e0-105">Single-line delimiter.</span></span> <span data-ttu-id="339e0-106">Jest to formularz, który jest wyświetlany w przykładach dokumentacji i używane przez szablony projektu Visual C#.</span><span class="sxs-lookup"><span data-stu-id="339e0-106">This is the form that is shown in documentation examples and used by the Visual C# project templates.</span></span> <span data-ttu-id="339e0-107">Jeśli po ograniczniku znajduje się znak odstępu, znak ten nie jest uwzględniany w danych wyjściowych XML.</span><span class="sxs-lookup"><span data-stu-id="339e0-107">If there is a white space character following the delimiter, that character is not included in the XML output.</span></span>

  > [!NOTE]
  > <span data-ttu-id="339e0-108">Ide programu Visual Studio ma funkcję o nazwie Inteligentna edycja komentarza, która automatycznie wstawia \<> podsumowania i \</summary> tagów i przenosi kursor w tych tagach po wpisaniu `///` ogranicznika w Edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="339e0-108">The Visual Studio IDE has a feature called Smart Comment Editing that automatically inserts the \<summary> and \</summary> tags and moves your cursor within these tags after you type the `///` delimiter in the Code Editor.</span></span> <span data-ttu-id="339e0-109">Tę funkcję można włączyć lub wyłączyć w [oknie dialogowym Opcje](/visualstudio/ide/reference/options-text-editor-csharp-advanced).</span><span class="sxs-lookup"><span data-stu-id="339e0-109">You can turn this feature on or off in the [Options dialog box](/visualstudio/ide/reference/options-text-editor-csharp-advanced).</span></span>
  
- `/** */`

  <span data-ttu-id="339e0-110">Wieloliniowe ograniczniki.</span><span class="sxs-lookup"><span data-stu-id="339e0-110">Multiline delimiters.</span></span>

  <span data-ttu-id="339e0-111">Istnieją pewne reguły formatowania, których należy `/** */` przestrzegać podczas korzystania z ograniczników:</span><span class="sxs-lookup"><span data-stu-id="339e0-111">There are some formatting rules to follow when you use the `/** */` delimiters:</span></span>
  
  - <span data-ttu-id="339e0-112">W wierszu zawierającym `/**` ogranicznik, jeśli pozostała część wiersza jest odstępem, wiersz nie jest przetwarzany dla komentarzy.</span><span class="sxs-lookup"><span data-stu-id="339e0-112">On the line that contains the `/**` delimiter, if the remainder of the line is white space, the line is not processed for comments.</span></span> <span data-ttu-id="339e0-113">Jeśli pierwszym znakiem `/**` po ograniczniku jest biały znak, ten znak odstępu jest ignorowany, a reszta wiersza jest przetwarzana.</span><span class="sxs-lookup"><span data-stu-id="339e0-113">If the first character after the `/**` delimiter is white space, that white space character is ignored and the rest of the line is processed.</span></span> <span data-ttu-id="339e0-114">W przeciwnym razie cały tekst `/**` wiersza po ogranicznik jest przetwarzany jako część komentarza.</span><span class="sxs-lookup"><span data-stu-id="339e0-114">Otherwise, the entire text of the line after the `/**` delimiter is processed as part of the comment.</span></span>

  - <span data-ttu-id="339e0-115">W wierszu zawierającym `*/` ogranicznik, jeśli istnieje tylko biały `*/` znak do ogranicznika, wiersz ten jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="339e0-115">On the line that contains the `*/` delimiter, if there is only white space up to the `*/` delimiter, that line is ignored.</span></span> <span data-ttu-id="339e0-116">W przeciwnym razie tekst w `*/` wierszu do ogranicznika jest przetwarzany jako część komentarza, z zastrzeżeniem reguł dopasowywania wzorców opisanych w poniższym punktorze.</span><span class="sxs-lookup"><span data-stu-id="339e0-116">Otherwise, the text on the line up to the `*/` delimiter is processed as part of the comment, subject to the pattern-matching rules described in the following bullet.</span></span>
  
  - <span data-ttu-id="339e0-117">Dla wierszy po tym, `/**` który zaczyna się od ogranicznika, kompilator szuka wspólnego wzorca na początku każdego wiersza.</span><span class="sxs-lookup"><span data-stu-id="339e0-117">For the lines after the one that begins with the `/**` delimiter, the compiler looks for a common pattern at the beginning of each line.</span></span> <span data-ttu-id="339e0-118">Wzór może składać się z opcjonalnego`*`odstępu i gwiazdki ( ), a następnie bardziej opcjonalnego odstępu.</span><span class="sxs-lookup"><span data-stu-id="339e0-118">The pattern can consist of optional white space and an asterisk (`*`), followed by more optional white space.</span></span> <span data-ttu-id="339e0-119">Jeśli kompilator znajdzie wspólny wzorzec na początku `/**` każdego wiersza, `*/` który nie zaczyna się od ogranicznika lub ogranicznika, ignoruje ten wzorzec dla każdego wiersza.</span><span class="sxs-lookup"><span data-stu-id="339e0-119">If the compiler finds a common pattern at the beginning of each line that does not begin with the `/**` delimiter or the `*/` delimiter, it ignores that pattern for each line.</span></span>

  <span data-ttu-id="339e0-120">Poniższe przykłady ilustrują te reguły.</span><span class="sxs-lookup"><span data-stu-id="339e0-120">The following examples illustrate these rules.</span></span>

  - <span data-ttu-id="339e0-121">Jedyną częścią następującego komentarza, który zostanie przetworzony, `<summary>`jest wiersz, który zaczyna się od .</span><span class="sxs-lookup"><span data-stu-id="339e0-121">The only part of the following comment that will be processed is the line that begins with `<summary>`.</span></span> <span data-ttu-id="339e0-122">Trzy formaty znaczników generują te same komentarze.</span><span class="sxs-lookup"><span data-stu-id="339e0-122">The three tag formats produce the same comments.</span></span>

    ```csharp
    /** <summary>text</summary> */

    /**
    <summary>text</summary>
    */

    /**
     * <summary>text</summary>
    */
    ```

  - <span data-ttu-id="339e0-123">Kompilator identyfikuje wspólny \* wzorzec " " na początku drugiego i trzeciego wiersza.</span><span class="sxs-lookup"><span data-stu-id="339e0-123">The compiler identifies a common pattern of " \* " at the beginning of the second and third lines.</span></span> <span data-ttu-id="339e0-124">Wzorzec nie jest uwzględniony w danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="339e0-124">The pattern is not included in the output.</span></span>

    ```csharp
    /**
     * <summary>
     * text </summary>*/
    ```

  - <span data-ttu-id="339e0-125">Kompilator nie znajdzie żadnego wspólnego wzorca w następującym komentarzu, ponieważ drugi znak w trzecim wierszu nie jest gwiazdką.</span><span class="sxs-lookup"><span data-stu-id="339e0-125">The compiler finds no common pattern in the following comment because the second character on the third line is not an asterisk.</span></span> <span data-ttu-id="339e0-126">W związku z tym cały tekst w drugim i trzecim wierszu jest przetwarzany jako część komentarza.</span><span class="sxs-lookup"><span data-stu-id="339e0-126">Therefore, all text on the second and third lines is processed as part of the comment.</span></span>

    ```csharp
    /**
     * <summary>
       text </summary>
    */
    ```

  - <span data-ttu-id="339e0-127">Kompilator nie znajdzie żadnego wzorca w następującym komentarzu z dwóch powodów.</span><span class="sxs-lookup"><span data-stu-id="339e0-127">The compiler finds no pattern in the following comment for two reasons.</span></span> <span data-ttu-id="339e0-128">Po pierwsze, liczba spacji przed gwiazdką nie jest spójna.</span><span class="sxs-lookup"><span data-stu-id="339e0-128">First, the number of spaces before the asterisk is not consistent.</span></span> <span data-ttu-id="339e0-129">Po drugie, piąta linia zaczyna się od karty, która nie pasuje do spacji.</span><span class="sxs-lookup"><span data-stu-id="339e0-129">Second, the fifth line begins with a tab, which does not match spaces.</span></span> <span data-ttu-id="339e0-130">W związku z tym cały tekst z wierszy od drugiego do piątego jest przetwarzany jako część komentarza.</span><span class="sxs-lookup"><span data-stu-id="339e0-130">Therefore, all text from lines two through five is processed as part of the comment.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="339e0-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="339e0-131">See also</span></span>

- [<span data-ttu-id="339e0-132">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="339e0-132">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="339e0-133">Komentarze dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="339e0-133">XML documentation comments</span></span>](./index.md)
- [<span data-ttu-id="339e0-134">-doc (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="339e0-134">-doc (C# compiler options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
