---
title: Analizowanie innych ciągów w programie .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Char data type, parsing strings
- enumerations [.NET Framework], parsing strings
- base types, parsing strings
- parsing strings, other strings
- Boolean data type, parsing strings
ms.assetid: d139bc00-3c4e-4d78-ac9a-5c951b258d28
ms.openlocfilehash: a3503e0e499c6010fcc3d8669fa5c1eaf2dbf570
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277547"
---
# <a name="parsing-other-strings-in-net"></a><span data-ttu-id="5e796-102">Analizowanie innych ciągów w programie .NET</span><span class="sxs-lookup"><span data-stu-id="5e796-102">Parsing Other Strings in .NET</span></span>
<span data-ttu-id="5e796-103">Oprócz liczb i <xref:System.DateTime> ciągów, można również analizować ciągi reprezentujące typy <xref:System.Char> , <xref:System.Boolean> i <xref:System.Enum> do typów danych.</span><span class="sxs-lookup"><span data-stu-id="5e796-103">In addition to numeric and <xref:System.DateTime> strings, you can also parse strings that represent the types <xref:System.Char>, <xref:System.Boolean>, and <xref:System.Enum> into data types.</span></span>  
  
## <a name="char"></a><span data-ttu-id="5e796-104">Char</span><span class="sxs-lookup"><span data-stu-id="5e796-104">Char</span></span>  
 <span data-ttu-id="5e796-105">Statyczna metoda analizy skojarzona z typem danych **char** jest przydatna do konwertowania ciągu, który zawiera pojedynczy znak do jego wartości Unicode.</span><span class="sxs-lookup"><span data-stu-id="5e796-105">The static parse method associated with the **Char** data type is useful for converting a string that contains a single character into its Unicode value.</span></span> <span data-ttu-id="5e796-106">Poniższy przykład kodu analizuje ciąg w znak Unicode.</span><span class="sxs-lookup"><span data-stu-id="5e796-106">The following code example parses a string into a Unicode character.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## <a name="boolean"></a><span data-ttu-id="5e796-107">Boolean (wartość logiczna)</span><span class="sxs-lookup"><span data-stu-id="5e796-107">Boolean</span></span>  
 <span data-ttu-id="5e796-108">Typ danych **Boolean** zawiera metodę **analizy** , której można użyć do przekonwertowania ciągu, który reprezentuje wartość logiczną w rzeczywistym typie **Boolean** .</span><span class="sxs-lookup"><span data-stu-id="5e796-108">The **Boolean** data type contains a **Parse** method that you can use to convert a string that represents a Boolean value into an actual **Boolean** type.</span></span> <span data-ttu-id="5e796-109">W tej metodzie nie jest rozróżniana wielkość liter i można pomyślnie przeanalizować ciąg zawierający wartość "true" lub "false".</span><span class="sxs-lookup"><span data-stu-id="5e796-109">This method is not case-sensitive and can successfully parse a string containing "True" or "False."</span></span> <span data-ttu-id="5e796-110">Metoda **Parse** skojarzona z typem **Boolean** może również analizować ciągi, które są ujęte w białe znaki.</span><span class="sxs-lookup"><span data-stu-id="5e796-110">The **Parse** method associated with the **Boolean** type can also parse strings that are surrounded by white spaces.</span></span> <span data-ttu-id="5e796-111">W przypadku przekazanie dowolnego innego ciągu <xref:System.FormatException> jest zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="5e796-111">If any other string is passed, a <xref:System.FormatException> is thrown.</span></span>  
  
 <span data-ttu-id="5e796-112">Poniższy przykład kodu używa metody **Parse** do przekonwertowania ciągu na wartość logiczną.</span><span class="sxs-lookup"><span data-stu-id="5e796-112">The following code example uses the **Parse** method to convert a string into a Boolean value.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## <a name="enumeration"></a><span data-ttu-id="5e796-113">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="5e796-113">Enumeration</span></span>  
 <span data-ttu-id="5e796-114">Możesz użyć statycznej metody **Parse** , aby zainicjować typ wyliczeniowy jako wartość ciągu.</span><span class="sxs-lookup"><span data-stu-id="5e796-114">You can use the static **Parse** method to initialize an enumeration type to the value of a string.</span></span> <span data-ttu-id="5e796-115">Ta metoda akceptuje analizowany typ wyliczeniowy, ciąg do przeanalizowania i opcjonalną flagę logiczną wskazującą, czy podczas analizy jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="5e796-115">This method accepts the enumeration type you are parsing, the string to parse, and an optional Boolean flag indicating whether or not the parse is case-sensitive.</span></span> <span data-ttu-id="5e796-116">Analizowany ciąg może zawierać kilka wartości rozdzielonych przecinkami, które mogą być poprzedzone lub po którym następuje jedna lub więcej pustych spacji (nazywanych również białymi spacjami).</span><span class="sxs-lookup"><span data-stu-id="5e796-116">The string you are parsing can contain several values separated by commas, which can be preceded or followed by one or more empty spaces (also called white spaces).</span></span> <span data-ttu-id="5e796-117">Gdy ciąg zawiera wiele wartości, wartość zwracanego obiektu jest wartością wszystkich określonych wartości połączonych z bitową lub operacją.</span><span class="sxs-lookup"><span data-stu-id="5e796-117">When the string contains multiple values, the value of the returned object is the value of all specified values combined with a bitwise OR operation.</span></span>  
  
 <span data-ttu-id="5e796-118">W poniższym przykładzie zastosowano metodę **Parse** do przekonwertowania ciągu na wartość wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5e796-118">The following example uses the **Parse** method to convert a string representation into an enumeration value.</span></span> <span data-ttu-id="5e796-119"><xref:System.DayOfWeek>Wyliczenie jest inicjowane w **czwartek** od ciągu.</span><span class="sxs-lookup"><span data-stu-id="5e796-119">The <xref:System.DayOfWeek> enumeration is initialized to **Thursday** from a string.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="5e796-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5e796-120">See also</span></span>

- [<span data-ttu-id="5e796-121">Analiza składniowa ciągów</span><span class="sxs-lookup"><span data-stu-id="5e796-121">Parsing Strings</span></span>](parsing-strings.md)
- [<span data-ttu-id="5e796-122">Formatowanie typów</span><span class="sxs-lookup"><span data-stu-id="5e796-122">Formatting Types</span></span>](formatting-types.md)
- [<span data-ttu-id="5e796-123">Konwersja typów w programie .NET</span><span class="sxs-lookup"><span data-stu-id="5e796-123">Type Conversion in the .NET</span></span>](type-conversion.md)
