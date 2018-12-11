---
title: Ograniczniki tagów dokumentacji - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
ms.openlocfilehash: ce6b23edb10733de3134b5233413de8b535c11ac
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235296"
---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a><span data-ttu-id="294ab-102">Ograniczniki tagów dokumentacji (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="294ab-102">Delimiters for Documentation Tags (C# Programming Guide)</span></span>
<span data-ttu-id="294ab-103">Użycie komentarze dokumentacji XML wymaga ograniczników, które wskazują kompilatora, gdzie rozpoczyna się i kończy w komentarzu dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="294ab-103">The use of XML doc comments requires delimiters, which indicate to the compiler where a documentation comment begins and ends.</span></span> <span data-ttu-id="294ab-104">Za pomocą następujących rodzajów ograniczniki tagów dokumentacji XML:</span><span class="sxs-lookup"><span data-stu-id="294ab-104">You can use the following kinds of delimiters with the XML documentation tags:</span></span>  
  
 `///`  
 <span data-ttu-id="294ab-105">Ogranicznik jeden wiersz.</span><span class="sxs-lookup"><span data-stu-id="294ab-105">Single-line delimiter.</span></span> <span data-ttu-id="294ab-106">Jest to forma, pokazano w przykładach dokumentacji i używane przez Szablony projektu Visual C#.</span><span class="sxs-lookup"><span data-stu-id="294ab-106">This is the form that is shown in documentation examples and used by the Visual C# project templates.</span></span> <span data-ttu-id="294ab-107">W przypadku biały znak po znaku ograniczającym ten znak nie znajduje się w danych wyjściowych XML.</span><span class="sxs-lookup"><span data-stu-id="294ab-107">If there is a white space character following the delimiter, that character is not included in the XML output.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="294ab-108">Środowiska IDE programu Visual Studio zawiera funkcję o nazwie inteligentne edytowanie komentarzy, automatycznie wstawi \<podsumowania > i \</summary > Znaczniki i przenosi kursor w ramach tych znaczników po wpisaniu `///` ogranicznika w edytorze kodu .</span><span class="sxs-lookup"><span data-stu-id="294ab-108">The Visual Studio IDE has a feature called Smart Comment Editing that automatically inserts the \<summary> and \</summary> tags and moves your cursor within these tags after you type the `///` delimiter in the Code Editor.</span></span> <span data-ttu-id="294ab-109">Można włączyć tę funkcję lub wyłączyć [okno dialogowe Opcje](/visualstudio/ide/reference/options-text-editor-csharp-advanced).</span><span class="sxs-lookup"><span data-stu-id="294ab-109">You can turn this feature on or off in the [Options dialog box](/visualstudio/ide/reference/options-text-editor-csharp-advanced).</span></span>  
  
 `/** */`  
 <span data-ttu-id="294ab-110">Wielowierszowy ograniczników.</span><span class="sxs-lookup"><span data-stu-id="294ab-110">Multiline delimiters.</span></span>  
  
 <span data-ttu-id="294ab-111">Istnieją pewne reguły formatowania do wykonania, gdy używasz `/** */` ograniczników.</span><span class="sxs-lookup"><span data-stu-id="294ab-111">There are some formatting rules to follow when you use the `/** */` delimiters.</span></span>  
  
-   <span data-ttu-id="294ab-112">W wierszu, który zawiera `/**` ogranicznik, jeśli pozostałą część wiersza jest biały znak, wiersz nie został przetworzony komentarzy.</span><span class="sxs-lookup"><span data-stu-id="294ab-112">On the line that contains the `/**` delimiter, if the remainder of the line is white space, the line is not processed for comments.</span></span> <span data-ttu-id="294ab-113">Jeśli pierwszy znak po `/**` ogranicznik jest odstępu, że biały znak jest ignorowana, a pozostała część wiersza jest przetwarzany.</span><span class="sxs-lookup"><span data-stu-id="294ab-113">If the first character after the `/**` delimiter is white space, that white space character is ignored and the rest of the line is processed.</span></span> <span data-ttu-id="294ab-114">W przeciwnym razie cały tekst wiersza po `/**` ogranicznik jest przetwarzany jako część komentarza.</span><span class="sxs-lookup"><span data-stu-id="294ab-114">Otherwise, the entire text of the line after the `/**` delimiter is processed as part of the comment.</span></span>  
  
-   <span data-ttu-id="294ab-115">W wierszu, który zawiera `*/` ogranicznik, jeśli występuje maksymalnie białych znaków `*/` ogranicznik, w tym wierszu jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="294ab-115">On the line that contains the `*/` delimiter, if there is only white space up to the `*/` delimiter, that line is ignored.</span></span> <span data-ttu-id="294ab-116">W przeciwnym razie tekst w wierszu do `*/` ogranicznik jest przetwarzany jako część komentarza, zgodnie z regułami dopasowywania wzorca opisanego w następny.</span><span class="sxs-lookup"><span data-stu-id="294ab-116">Otherwise, the text on the line up to the `*/` delimiter is processed as part of the comment, subject to the pattern-matching rules described in the following bullet.</span></span>  
  
-   <span data-ttu-id="294ab-117">Wiersze po ten, który rozpoczyna się od `/**` ogranicznik, kompilator szuka wspólny wzorzec na początku każdego wiersza.</span><span class="sxs-lookup"><span data-stu-id="294ab-117">For the lines after the one that begins with the `/**` delimiter, the compiler looks for a common pattern at the beginning of each line.</span></span> <span data-ttu-id="294ab-118">Wzorzec może zawierać opcjonalny odstęp i znak gwiazdki (`*`), a następnie więcej opcjonalny odstęp.</span><span class="sxs-lookup"><span data-stu-id="294ab-118">The pattern can consist of optional white space and an asterisk (`*`), followed by more optional white space.</span></span> <span data-ttu-id="294ab-119">Jeśli kompilator znajdzie wspólny wzorzec na początku każdego wiersza, który nie zaczyna się od `/**` ogranicznik lub `*/` ogranicznika ignoruje tego wzorca dla każdego wiersza.</span><span class="sxs-lookup"><span data-stu-id="294ab-119">If the compiler finds a common pattern at the beginning of each line that does not begin with the `/**` delimiter or the `*/` delimiter, it ignores that pattern for each line.</span></span>  
  
 <span data-ttu-id="294ab-120">Poniższe przykłady ilustrują tych reguł.</span><span class="sxs-lookup"><span data-stu-id="294ab-120">The following examples illustrate these rules.</span></span>  
  
-   <span data-ttu-id="294ab-121">To jedyna część Poniższy komentarz, które będą przetwarzane jest wiersz, który rozpoczyna się od `<summary>`.</span><span class="sxs-lookup"><span data-stu-id="294ab-121">The only part of the following comment that will be processed is the line that begins with `<summary>`.</span></span> <span data-ttu-id="294ab-122">Formaty trzech etykiet generuje ten sam komentarzy.</span><span class="sxs-lookup"><span data-stu-id="294ab-122">The three tag formats produce the same comments.</span></span>  
  
    ```  
    /** <summary>text</summary> */   
  
    /**   
    <summary>text</summary>   
    */   
  
    /**   
     * <summary>text</summary>   
    */  
    ```  
  
-   <span data-ttu-id="294ab-123">Kompilator identyfikuje wspólny wzorzec "\*" na początku linii drugiego i trzeciego.</span><span class="sxs-lookup"><span data-stu-id="294ab-123">The compiler identifies a common pattern of " \* " at the beginning of the second and third lines.</span></span> <span data-ttu-id="294ab-124">Wzorzec jest niedostępna w danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="294ab-124">The pattern is not included in the output.</span></span>  
  
    ```  
    /**   
     * <summary>   
     * text </summary>*/   
    ```  
  
-   <span data-ttu-id="294ab-125">Kompilator znajdzie nie wspólny wzorzec w poniższy komentarz, ponieważ drugim znakiem w trzecim wierszu nie jest znak gwiazdki.</span><span class="sxs-lookup"><span data-stu-id="294ab-125">The compiler finds no common pattern in the following comment because the second character on the third line is not an asterisk.</span></span> <span data-ttu-id="294ab-126">W związku z tym cały tekst w wierszach drugiej i trzeciej są przetwarzane w ramach komentarza.</span><span class="sxs-lookup"><span data-stu-id="294ab-126">Therefore, all text on the second and third lines is processed as part of the comment.</span></span>  
  
    ```  
    /**   
     * <summary>   
       text </summary>  
    */   
    ```  
  
-   <span data-ttu-id="294ab-127">Kompilator znajdzie nie wzorca w poniższy komentarz z dwóch przyczyn.</span><span class="sxs-lookup"><span data-stu-id="294ab-127">The compiler finds no pattern in the following comment for two reasons.</span></span> <span data-ttu-id="294ab-128">Po pierwsze liczbę spacji przed gwiazdka nie jest spójna.</span><span class="sxs-lookup"><span data-stu-id="294ab-128">First, the number of spaces before the asterisk is not consistent.</span></span> <span data-ttu-id="294ab-129">Po drugie piąty wiersz rozpoczyna się od kartę, która jest niezgodna z miejsc do magazynowania.</span><span class="sxs-lookup"><span data-stu-id="294ab-129">Second, the fifth line begins with a tab, which does not match spaces.</span></span> <span data-ttu-id="294ab-130">W związku z tym cały tekst z dwóch wierszy, za pośrednictwem pięciu osób są przetwarzane jako część komentarza.</span><span class="sxs-lookup"><span data-stu-id="294ab-130">Therefore, all text from lines two through five is processed as part of the comment.</span></span>  
  
    ```  
    /**   
      * <summary>   
      * text   
     *  text2   
        *  </summary>   
    */   
    ```  
  
## <a name="see-also"></a><span data-ttu-id="294ab-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="294ab-131">See Also</span></span>

- [<span data-ttu-id="294ab-132">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="294ab-132">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="294ab-133">Komentarze dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="294ab-133">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)  
- [<span data-ttu-id="294ab-134">/ doc (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="294ab-134">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
- [<span data-ttu-id="294ab-135">Komentarze dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="294ab-135">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
