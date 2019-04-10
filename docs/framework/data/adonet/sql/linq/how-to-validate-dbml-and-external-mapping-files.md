---
title: 'Instrukcje: Weryfikacja DBML i zewnętrznych plików mapowania'
ms.date: 03/30/2017
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
ms.openlocfilehash: 83a26f22495c849aa00143ca36b63fa147120c28
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310242"
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a><span data-ttu-id="fdc49-102">Instrukcje: Weryfikacja DBML i zewnętrznych plików mapowania</span><span class="sxs-lookup"><span data-stu-id="fdc49-102">How to: Validate DBML and External Mapping Files</span></span>
<span data-ttu-id="fdc49-103">Mapowanie zewnętrzne pliki i pliki dbml zmodyfikujesz musi być weryfikowany pod kątem ich definicji schematu odpowiednich.</span><span class="sxs-lookup"><span data-stu-id="fdc49-103">External mapping files and .dbml files that you modify must be validated against their respective schema definitions.</span></span> <span data-ttu-id="fdc49-104">Ten temat zawiera użytkowników programu Visual Studio wykonując kroki do zaimplementowania procesu weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="fdc49-104">This topic provides Visual Studio users with the steps to implement the validation process.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
### <a name="to-validate-a-dbml-or-xml-file"></a><span data-ttu-id="fdc49-105">Aby sprawdzić poprawność dbml lub plik XML</span><span class="sxs-lookup"><span data-stu-id="fdc49-105">To validate a .dbml or XML file</span></span>  
  
1. <span data-ttu-id="fdc49-106">W programie Visual Studio **pliku** menu wskaż **Otwórz**, a następnie kliknij przycisk **pliku**.</span><span class="sxs-lookup"><span data-stu-id="fdc49-106">On the Visual Studio **File** menu, point to **Open**, and then click **File**.</span></span>  
  
2. <span data-ttu-id="fdc49-107">W **Otwórz plik** okna dialogowego kliknij dbml lub plik mapowania XML, który chcesz zweryfikować.</span><span class="sxs-lookup"><span data-stu-id="fdc49-107">In the **Open File** dialog box, click the .dbml or XML mapping file that you want to validate.</span></span>  
  
     <span data-ttu-id="fdc49-108">Plik zostanie otwarty w **edytora XML**.</span><span class="sxs-lookup"><span data-stu-id="fdc49-108">The file opens in the **XML Editor**.</span></span>  
  
3. <span data-ttu-id="fdc49-109">Kliknij prawym przyciskiem myszy okno, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="fdc49-109">Right-click the window, and then click **Properties**.</span></span>  
  
4. <span data-ttu-id="fdc49-110">W **właściwości** okna, kliknij przycisk wielokropka dla **schematów** właściwości.</span><span class="sxs-lookup"><span data-stu-id="fdc49-110">In the **Properties** window, click the ellipsis for the **Schemas** property.</span></span>  
  
     <span data-ttu-id="fdc49-111">**Schematów XML** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="fdc49-111">The **XML Schemas** dialog box opens.</span></span>  
  
5. <span data-ttu-id="fdc49-112">Należy zauważyć definicji schematu odpowiednie do określonych celów.</span><span class="sxs-lookup"><span data-stu-id="fdc49-112">Note the appropriate schema definition for your purpose.</span></span>  
  
    -   <span data-ttu-id="fdc49-113">DbmlSchema.xsd jest definicja schematu dla sprawdzanie poprawności pliku dbml.</span><span class="sxs-lookup"><span data-stu-id="fdc49-113">DbmlSchema.xsd is the schema definition for validating a .dbml file.</span></span> <span data-ttu-id="fdc49-114">Aby uzyskać więcej informacji, zobacz [generowanie kodu w składniku LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="fdc49-114">For more information, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
    -   <span data-ttu-id="fdc49-115">LinqToSqlMapping.xsd jest definicja schematu dla weryfikowania plik mapowania XML.</span><span class="sxs-lookup"><span data-stu-id="fdc49-115">LinqToSqlMapping.xsd is the schema definition for validating an external XML mapping file.</span></span> <span data-ttu-id="fdc49-116">Aby uzyskać więcej informacji, zobacz [mapowanie zewnętrzne](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="fdc49-116">For more information, see [External Mapping](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span></span>  
  
6. <span data-ttu-id="fdc49-117">W **użyj** kolumnę żądany schemat definicji wiersza, kliknij, aby otworzyć pole listy rozwijanej, a następnie kliknij przycisk **używają tego schematu**.</span><span class="sxs-lookup"><span data-stu-id="fdc49-117">In the **Use** column of the desired schema definition row, click to open the drop-down box, and then click **Use this schema**.</span></span>  
  
     <span data-ttu-id="fdc49-118">Plik definicji schematu jest teraz skojarzone z Twojej DBML lub mapowania pliku XML.</span><span class="sxs-lookup"><span data-stu-id="fdc49-118">The schema definition file is now associated with your DBML or XML mapping file.</span></span>  
  
     <span data-ttu-id="fdc49-119">Upewnij się, że nie zaznaczono żadnych definicji schematu.</span><span class="sxs-lookup"><span data-stu-id="fdc49-119">Make sure no other schema definitions are selected.</span></span>  
  
7. <span data-ttu-id="fdc49-120">Na **widoku** menu, kliknij przycisk **lista błędów**.</span><span class="sxs-lookup"><span data-stu-id="fdc49-120">On the **View** menu, click **Error List**.</span></span>  
  
     <span data-ttu-id="fdc49-121">Ustal, czy zostały wygenerowane błędy, ostrzeżenia lub komunikaty.</span><span class="sxs-lookup"><span data-stu-id="fdc49-121">Determine whether errors, warnings, or messages have been generated.</span></span> <span data-ttu-id="fdc49-122">Jeśli nie, plik XML jest nieprawidłowa względem definicji schematu.</span><span class="sxs-lookup"><span data-stu-id="fdc49-122">If not, the XML file is valid against the schema definition.</span></span>  
  
## <a name="alternate-method-for-supplying-schema-definition"></a><span data-ttu-id="fdc49-123">Alternatywna metoda dla podanie definicji schematu</span><span class="sxs-lookup"><span data-stu-id="fdc49-123">Alternate Method for Supplying Schema Definition</span></span>  
 <span data-ttu-id="fdc49-124">Jeśli z jakiegoś powodu XSD odpowiedniego pliku nie jest wyświetlana w **schematów XML** okno dialogowe, możesz pobrać plik XSD z tematu Pomocy.</span><span class="sxs-lookup"><span data-stu-id="fdc49-124">If for some reason the appropriate .xsd file does not appear in the **XML Schemas** dialog box, you can download the .xsd file from a Help topic.</span></span> <span data-ttu-id="fdc49-125">Poniższe etapy ułatwiają przeprowadzenie Zapisz pobrany plik w formacie Unicode, wymagane przez edytorze XML programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fdc49-125">The following steps help you save the downloaded file in the Unicode format required by the Visual Studio XML Editor.</span></span>  
  
#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a><span data-ttu-id="fdc49-126">Aby skopiować plik definicji schematu z tematu Pomocy.</span><span class="sxs-lookup"><span data-stu-id="fdc49-126">To copy a schema definition file from a Help topic</span></span>  
  
1. <span data-ttu-id="fdc49-127">Lokalizowanie tematu pomocy, który zawiera definicję schematu, zgodnie z opisem we wcześniejszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="fdc49-127">Locate the Help topic that contains the schema definition as described earlier in this topic.</span></span>  
  
    -   <span data-ttu-id="fdc49-128">W przypadku plików dbml, zobacz [generowanie kodu w składniku LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="fdc49-128">For .dbml files, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
    -   <span data-ttu-id="fdc49-129">Aby uzyskać zewnętrznych plików mapowania, zobacz [mapowanie zewnętrzne](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="fdc49-129">For external mapping files, see [External Mapping](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span></span>  
  
2. <span data-ttu-id="fdc49-130">Kliknij przycisk **Kopiuj kod** można skopiować pliku kod do Schowka.</span><span class="sxs-lookup"><span data-stu-id="fdc49-130">Click **Copy Code** to copy the code file to the Clipboard.</span></span>  
  
3. <span data-ttu-id="fdc49-131">Uruchom program Notatnik, aby utworzyć nowy plik.</span><span class="sxs-lookup"><span data-stu-id="fdc49-131">Start Notepad to create a new file.</span></span>  
  
4. <span data-ttu-id="fdc49-132">Wklej kod ze Schowka do Notatnika.</span><span class="sxs-lookup"><span data-stu-id="fdc49-132">Paste the code from the clipboard into Notepad file.</span></span>  
  
5. <span data-ttu-id="fdc49-133">W programie Notatnik **pliku** menu, kliknij przycisk **Zapisz jako**.</span><span class="sxs-lookup"><span data-stu-id="fdc49-133">On the Notepad **File** menu, click **Save As**.</span></span>  
  
6. <span data-ttu-id="fdc49-134">W **kodowanie** wybierz opcję **Unicode**.</span><span class="sxs-lookup"><span data-stu-id="fdc49-134">In the **Encoding** box, select **Unicode**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="fdc49-135">Wybranie tej opcji gwarantuje, że znacznika kolejności bajtów Unicode-16 (`FFFE`) jest dołączony do pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="fdc49-135">This selection guarantees that the Unicode-16 byte-order marker (`FFFE`) is prepended to the text file.</span></span>  
  
7. <span data-ttu-id="fdc49-136">W **nazwy pliku** Utwórz nazwę pliku z rozszerzeniem xsd.</span><span class="sxs-lookup"><span data-stu-id="fdc49-136">In the **File name** box, create a file name with an .xsd extension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdc49-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fdc49-137">See also</span></span>

- [<span data-ttu-id="fdc49-138">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="fdc49-138">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
