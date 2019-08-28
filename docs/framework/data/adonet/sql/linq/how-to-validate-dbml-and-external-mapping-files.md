---
title: 'Instrukcje: Weryfikacja DBML i zewnętrznych plików mapowania'
ms.date: 03/30/2017
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
ms.openlocfilehash: 212d65dfe998b825dd40e564756083ed685dff6f
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041132"
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a><span data-ttu-id="63568-102">Instrukcje: Weryfikacja DBML i zewnętrznych plików mapowania</span><span class="sxs-lookup"><span data-stu-id="63568-102">How to: Validate DBML and External Mapping Files</span></span>

<span data-ttu-id="63568-103">Pliki mapowania zewnętrznego i pliki. dbml, które należy zmodyfikować, muszą być zweryfikowane pod kątem odpowiednich definicji schematu.</span><span class="sxs-lookup"><span data-stu-id="63568-103">External mapping files and .dbml files that you modify must be validated against their respective schema definitions.</span></span> <span data-ttu-id="63568-104">Ten temat zawiera informacje o użytkownikach programu Visual Studio z krokami w celu zaimplementowania procesu walidacji.</span><span class="sxs-lookup"><span data-stu-id="63568-104">This topic provides Visual Studio users with the steps to implement the validation process.</span></span>

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

### <a name="to-validate-a-dbml-or-xml-file"></a><span data-ttu-id="63568-105">Aby sprawdzić poprawność pliku. dbml lub XML</span><span class="sxs-lookup"><span data-stu-id="63568-105">To validate a .dbml or XML file</span></span>

1. <span data-ttu-id="63568-106">W menu **plik** programu Visual Studio wskaż polecenie **Otwórz**, a następnie kliknij pozycję **plik**.</span><span class="sxs-lookup"><span data-stu-id="63568-106">On the Visual Studio **File** menu, point to **Open**, and then click **File**.</span></span>

2. <span data-ttu-id="63568-107">W oknie dialogowym **Otwórz plik** kliknij plik mapowania dbml lub XML, który chcesz zweryfikować.</span><span class="sxs-lookup"><span data-stu-id="63568-107">In the **Open File** dialog box, click the .dbml or XML mapping file that you want to validate.</span></span>

    <span data-ttu-id="63568-108">Plik zostanie otwarty w **edytorze XML**.</span><span class="sxs-lookup"><span data-stu-id="63568-108">The file opens in the **XML Editor**.</span></span>

3. <span data-ttu-id="63568-109">Kliknij okno prawym przyciskiem myszy, a następnie kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="63568-109">Right-click the window, and then click **Properties**.</span></span>

4. <span data-ttu-id="63568-110">W oknie **Właściwości** kliknij wielokropek dla właściwości **schematy** .</span><span class="sxs-lookup"><span data-stu-id="63568-110">In the **Properties** window, click the ellipsis for the **Schemas** property.</span></span>

    <span data-ttu-id="63568-111">Zostanie otwarte okno dialogowe **schematy XML** .</span><span class="sxs-lookup"><span data-stu-id="63568-111">The **XML Schemas** dialog box opens.</span></span>

5. <span data-ttu-id="63568-112">Zanotuj odpowiednią definicję schematu dla danego celu.</span><span class="sxs-lookup"><span data-stu-id="63568-112">Note the appropriate schema definition for your purpose.</span></span>

    - <span data-ttu-id="63568-113">DbmlSchema. xsd jest definicją schematu służącą do walidacji pliku. dbml.</span><span class="sxs-lookup"><span data-stu-id="63568-113">DbmlSchema.xsd is the schema definition for validating a .dbml file.</span></span> <span data-ttu-id="63568-114">Aby uzyskać więcej informacji, zobacz [generowanie kodu w LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="63568-114">For more information, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>

    - <span data-ttu-id="63568-115">LinqToSqlMapping. xsd jest definicją schematu służącą do walidacji zewnętrznego pliku mapowania XML.</span><span class="sxs-lookup"><span data-stu-id="63568-115">LinqToSqlMapping.xsd is the schema definition for validating an external XML mapping file.</span></span> <span data-ttu-id="63568-116">Aby uzyskać więcej informacji, zobacz [Mapowanie zewnętrzne](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="63568-116">For more information, see [External Mapping](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span></span>

6. <span data-ttu-id="63568-117">W kolumnie **Użyj** w żądanym wierszu definicji schematu kliknij, aby otworzyć pole listy rozwijanej, a następnie kliknij pozycję **Użyj tego schematu**.</span><span class="sxs-lookup"><span data-stu-id="63568-117">In the **Use** column of the desired schema definition row, click to open the drop-down box, and then click **Use this schema**.</span></span>

    <span data-ttu-id="63568-118">Plik definicji schematu jest teraz skojarzony z plikiem mapowania DBML lub XML.</span><span class="sxs-lookup"><span data-stu-id="63568-118">The schema definition file is now associated with your DBML or XML mapping file.</span></span>

    <span data-ttu-id="63568-119">Upewnij się, że nie wybrano żadnych innych definicji schematu.</span><span class="sxs-lookup"><span data-stu-id="63568-119">Make sure no other schema definitions are selected.</span></span>

7. <span data-ttu-id="63568-120">W menu **Widok** kliknij **Lista błędów**.</span><span class="sxs-lookup"><span data-stu-id="63568-120">On the **View** menu, click **Error List**.</span></span>

    <span data-ttu-id="63568-121">Należy określić, czy zostały wygenerowane błędy, ostrzeżenia lub komunikaty.</span><span class="sxs-lookup"><span data-stu-id="63568-121">Determine whether errors, warnings, or messages have been generated.</span></span> <span data-ttu-id="63568-122">W przeciwnym razie plik XML jest prawidłowy względem definicji schematu.</span><span class="sxs-lookup"><span data-stu-id="63568-122">If not, the XML file is valid against the schema definition.</span></span>

## <a name="alternate-method-for-supplying-schema-definition"></a><span data-ttu-id="63568-123">Alternatywna metoda dostarczania definicji schematu</span><span class="sxs-lookup"><span data-stu-id="63568-123">Alternate Method for Supplying Schema Definition</span></span>

<span data-ttu-id="63568-124">Jeśli z jakiegoś powodu odpowiedni plik XSD nie jest wyświetlany w oknie dialogowym **schematy XML** , można pobrać plik XSD z tematu pomocy.</span><span class="sxs-lookup"><span data-stu-id="63568-124">If for some reason the appropriate .xsd file does not appear in the **XML Schemas** dialog box, you can download the .xsd file from a Help topic.</span></span> <span data-ttu-id="63568-125">Poniższe kroki ułatwiają zapisanie pobranego pliku w formacie Unicode wymaganym przez Edytor XML programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="63568-125">The following steps help you save the downloaded file in the Unicode format required by the Visual Studio XML Editor.</span></span>

#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a><span data-ttu-id="63568-126">Aby skopiować plik definicji schematu z tematu pomocy</span><span class="sxs-lookup"><span data-stu-id="63568-126">To copy a schema definition file from a Help topic</span></span>

1. <span data-ttu-id="63568-127">Znajdź temat pomocy zawierający definicję schematu, jak opisano wcześniej w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="63568-127">Locate the Help topic that contains the schema definition as described earlier in this topic.</span></span>

    - <span data-ttu-id="63568-128">Aby uzyskać pliki. dbml, zobacz [generowanie kodu w LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="63568-128">For .dbml files, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>

    - <span data-ttu-id="63568-129">W przypadku zewnętrznych plików mapowania zobacz [Mapowanie zewnętrzne](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="63568-129">For external mapping files, see [External Mapping](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span></span>

2. <span data-ttu-id="63568-130">Kliknij przycisk **Kopiuj kod** , aby skopiować plik kodu do Schowka.</span><span class="sxs-lookup"><span data-stu-id="63568-130">Click **Copy Code** to copy the code file to the Clipboard.</span></span>

3. <span data-ttu-id="63568-131">Uruchom Notatnik, aby utworzyć nowy plik.</span><span class="sxs-lookup"><span data-stu-id="63568-131">Start Notepad to create a new file.</span></span>

4. <span data-ttu-id="63568-132">Wklej kod ze schowka do pliku Notatnika.</span><span class="sxs-lookup"><span data-stu-id="63568-132">Paste the code from the clipboard into Notepad file.</span></span>

5. <span data-ttu-id="63568-133">W menu **plik** Notatnika kliknij przycisk **Zapisz jako**.</span><span class="sxs-lookup"><span data-stu-id="63568-133">On the Notepad **File** menu, click **Save As**.</span></span>

6. <span data-ttu-id="63568-134">W polu **kodowanie** wybierz opcję **Unicode**.</span><span class="sxs-lookup"><span data-stu-id="63568-134">In the **Encoding** box, select **Unicode**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="63568-135">Wybranie tej opcji gwarantuje, że znacznik kolejności bajtów Unicode-16 (`FFFE`) jest poprzedzony plikiem tekstowym.</span><span class="sxs-lookup"><span data-stu-id="63568-135">This selection guarantees that the Unicode-16 byte-order marker (`FFFE`) is prepended to the text file.</span></span>

7. <span data-ttu-id="63568-136">W polu **Nazwa pliku** Utwórz nazwę pliku z rozszerzeniem XSD.</span><span class="sxs-lookup"><span data-stu-id="63568-136">In the **File name** box, create a file name with an .xsd extension.</span></span>

## <a name="see-also"></a><span data-ttu-id="63568-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="63568-137">See also</span></span>

- [<span data-ttu-id="63568-138">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="63568-138">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
