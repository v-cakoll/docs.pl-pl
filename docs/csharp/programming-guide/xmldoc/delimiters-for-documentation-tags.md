---
title: Ograniczniki tagów dokumentacji - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
ms.openlocfilehash: d08dd0c68a11ddf73c19a1e09bc8c59937708553
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634767"
---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a><span data-ttu-id="49761-102">Ograniczniki znaczników dokumentacji (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="49761-102">Delimiters for Documentation Tags (C# Programming Guide)</span></span>
<span data-ttu-id="49761-103">Użycie komentarze dokumentacji XML wymaga ograniczników, które wskazują kompilatora, gdzie rozpoczyna się i kończy w komentarzu dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="49761-103">The use of XML doc comments requires delimiters, which indicate to the compiler where a documentation comment begins and ends.</span></span> <span data-ttu-id="49761-104">Za pomocą następujących rodzajów ograniczniki tagów dokumentacji XML:</span><span class="sxs-lookup"><span data-stu-id="49761-104">You can use the following kinds of delimiters with the XML documentation tags:</span></span>  
  
 `///`  
 <span data-ttu-id="49761-105">Ogranicznik jeden wiersz.</span><span class="sxs-lookup"><span data-stu-id="49761-105">Single-line delimiter.</span></span> <span data-ttu-id="49761-106">Jest to forma, pokazano w przykładach dokumentacji i używane przez Szablony projektu Visual C#.</span><span class="sxs-lookup"><span data-stu-id="49761-106">This is the form that is shown in documentation examples and used by the Visual C# project templates.</span></span> <span data-ttu-id="49761-107">W przypadku biały znak po znaku ograniczającym ten znak nie znajduje się w danych wyjściowych XML.</span><span class="sxs-lookup"><span data-stu-id="49761-107">If there is a white space character following the delimiter, that character is not included in the XML output.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49761-108">Środowiska IDE programu Visual Studio zawiera funkcję o nazwie inteligentne edytowanie komentarzy, automatycznie wstawi \<podsumowania > i \</summary > Znaczniki i przenosi kursor w ramach tych znaczników po wpisaniu `///` ogranicznika w edytorze kodu .</span><span class="sxs-lookup"><span data-stu-id="49761-108">The Visual Studio IDE has a feature called Smart Comment Editing that automatically inserts the \<summary> and \</summary> tags and moves your cursor within these tags after you type the `///` delimiter in the Code Editor.</span></span> <span data-ttu-id="49761-109">Można włączyć tę funkcję lub wyłączyć [okno dialogowe Opcje](/visualstudio/ide/reference/options-text-editor-csharp-advanced).</span><span class="sxs-lookup"><span data-stu-id="49761-109">You can turn this feature on or off in the [Options dialog box](/visualstudio/ide/reference/options-text-editor-csharp-advanced).</span></span>  
  
 `/** */`  
 <span data-ttu-id="49761-110">Wielowierszowy ograniczników.</span><span class="sxs-lookup"><span data-stu-id="49761-110">Multiline delimiters.</span></span>  
  
 <span data-ttu-id="49761-111">Istnieją pewne reguły formatowania do wykonania, gdy używasz `/** */` ograniczników.</span><span class="sxs-lookup"><span data-stu-id="49761-111">There are some formatting rules to follow when you use the `/** */` delimiters.</span></span>  
  
- <span data-ttu-id="49761-112">W wierszu, który zawiera `/**` ogranicznik, jeśli pozostałą część wiersza jest biały znak, wiersz nie został przetworzony komentarzy.</span><span class="sxs-lookup"><span data-stu-id="49761-112">On the line that contains the `/**` delimiter, if the remainder of the line is white space, the line is not processed for comments.</span></span> <span data-ttu-id="49761-113">Jeśli pierwszy znak po `/**` ogranicznik jest odstępu, że biały znak jest ignorowana, a pozostała część wiersza jest przetwarzany.</span><span class="sxs-lookup"><span data-stu-id="49761-113">If the first character after the `/**` delimiter is white space, that white space character is ignored and the rest of the line is processed.</span></span> <span data-ttu-id="49761-114">W przeciwnym razie cały tekst wiersza po `/**` ogranicznik jest przetwarzany jako część komentarza.</span><span class="sxs-lookup"><span data-stu-id="49761-114">Otherwise, the entire text of the line after the `/**` delimiter is processed as part of the comment.</span></span>  
  
- <span data-ttu-id="49761-115">W wierszu, który zawiera `*/` ogranicznik, jeśli występuje maksymalnie białych znaków `*/` ogranicznik, w tym wierszu jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="49761-115">On the line that contains the `*/` delimiter, if there is only white space up to the `*/` delimiter, that line is ignored.</span></span> <span data-ttu-id="49761-116">W przeciwnym razie tekst w wierszu do `*/` ogranicznik jest przetwarzany jako część komentarza, zgodnie z regułami dopasowywania wzorca opisanego w następny.</span><span class="sxs-lookup"><span data-stu-id="49761-116">Otherwise, the text on the line up to the `*/` delimiter is processed as part of the comment, subject to the pattern-matching rules described in the following bullet.</span></span>  
  
- <span data-ttu-id="49761-117">Wiersze po ten, który rozpoczyna się od `/**` ogranicznik, kompilator szuka wspólny wzorzec na początku każdego wiersza.</span><span class="sxs-lookup"><span data-stu-id="49761-117">For the lines after the one that begins with the `/**` delimiter, the compiler looks for a common pattern at the beginning of each line.</span></span> <span data-ttu-id="49761-118">Wzorzec może zawierać opcjonalny odstęp i znak gwiazdki (`*`), a następnie więcej opcjonalny odstęp.</span><span class="sxs-lookup"><span data-stu-id="49761-118">The pattern can consist of optional white space and an asterisk (`*`), followed by more optional white space.</span></span> <span data-ttu-id="49761-119">Jeśli kompilator znajdzie wspólny wzorzec na początku każdego wiersza, który nie zaczyna się od `/**` ogranicznik lub `*/` ogranicznika ignoruje tego wzorca dla każdego wiersza.</span><span class="sxs-lookup"><span data-stu-id="49761-119">If the compiler finds a common pattern at the beginning of each line that does not begin with the `/**` delimiter or the `*/` delimiter, it ignores that pattern for each line.</span></span>  
  
 <span data-ttu-id="49761-120">Poniższe przykłady ilustrują tych reguł.</span><span class="sxs-lookup"><span data-stu-id="49761-120">The following examples illustrate these rules.</span></span>  
  
- <span data-ttu-id="49761-121">To jedyna część Poniższy komentarz, które będą przetwarzane jest wiersz, który rozpoczyna się od `<summary>`.</span><span class="sxs-lookup"><span data-stu-id="49761-121">The only part of the following comment that will be processed is the line that begins with `<summary>`.</span></span> <span data-ttu-id="49761-122">Formaty trzech etykiet generuje ten sam komentarzy.</span><span class="sxs-lookup"><span data-stu-id="49761-122">The three tag formats produce the same comments.</span></span>  
  
    ```csharp  
    /** <summary>text</summary> */   
  
    /**   
    <summary>text</summary>   
    */   
  
    /**   
     * <summary>text</summary>   
    */  
    ```  
  
- <span data-ttu-id="49761-123">Kompilator identyfikuje wspólny wzorzec "\*" na początku linii drugiego i trzeciego.</span><span class="sxs-lookup"><span data-stu-id="49761-123">The compiler identifies a common pattern of " \* " at the beginning of the second and third lines.</span></span> <span data-ttu-id="49761-124">Wzorzec jest niedostępna w danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="49761-124">The pattern is not included in the output.</span></span>  
  
    ```csharp  
    /**   
     * <summary>   
     * text </summary>*/   
    ```  
  
- <span data-ttu-id="49761-125">Kompilator znajdzie nie wspólny wzorzec w poniższy komentarz, ponieważ drugim znakiem w trzecim wierszu nie jest znak gwiazdki.</span><span class="sxs-lookup"><span data-stu-id="49761-125">The compiler finds no common pattern in the following comment because the second character on the third line is not an asterisk.</span></span> <span data-ttu-id="49761-126">W związku z tym cały tekst w wierszach drugiej i trzeciej są przetwarzane w ramach komentarza.</span><span class="sxs-lookup"><span data-stu-id="49761-126">Therefore, all text on the second and third lines is processed as part of the comment.</span></span>  
  
    ```csharp  
    /**   
     * <summary>   
       text </summary>  
    */   
    ```  
  
- <span data-ttu-id="49761-127">Kompilator znajdzie nie wzorca w poniższy komentarz z dwóch przyczyn.</span><span class="sxs-lookup"><span data-stu-id="49761-127">The compiler finds no pattern in the following comment for two reasons.</span></span> <span data-ttu-id="49761-128">Po pierwsze liczbę spacji przed gwiazdka nie jest spójna.</span><span class="sxs-lookup"><span data-stu-id="49761-128">First, the number of spaces before the asterisk is not consistent.</span></span> <span data-ttu-id="49761-129">Po drugie piąty wiersz rozpoczyna się od kartę, która jest niezgodna z miejsc do magazynowania.</span><span class="sxs-lookup"><span data-stu-id="49761-129">Second, the fifth line begins with a tab, which does not match spaces.</span></span> <span data-ttu-id="49761-130">W związku z tym cały tekst z dwóch wierszy, za pośrednictwem pięciu osób są przetwarzane jako część komentarza.</span><span class="sxs-lookup"><span data-stu-id="49761-130">Therefore, all text from lines two through five is processed as part of the comment.</span></span>  
  
    ```csharp  
    /**   
      * <summary>   
      * text   
     *  text2   
        *  </summary>   
    */   
    ```  
  
## <a name="see-also"></a><span data-ttu-id="49761-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="49761-131">See also</span></span>

- [<span data-ttu-id="49761-132">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="49761-132">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="49761-133">Komentarze dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="49761-133">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/index.md)
- [<span data-ttu-id="49761-134">/ doc (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="49761-134">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="49761-135">Komentarze dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="49761-135">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/index.md)
