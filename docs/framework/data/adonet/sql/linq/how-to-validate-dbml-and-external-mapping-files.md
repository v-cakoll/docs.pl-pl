---
title: 'Porady: Sprawdzanie poprawności DBML i plikami zewnętrznych mapowania'
ms.date: 03/30/2017
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
ms.openlocfilehash: 9bf21353aebd0ae57c51b2ddf3b31b5e7f1ac615
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362165"
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a><span data-ttu-id="1f22b-102">Porady: Sprawdzanie poprawności DBML i plikami zewnętrznych mapowania</span><span class="sxs-lookup"><span data-stu-id="1f22b-102">How to: Validate DBML and External Mapping Files</span></span>
<span data-ttu-id="1f22b-103">Mapowanie zewnętrzne pliki i pliki .dbml zmodyfikowaniu musi zostać zweryfikowany względem ich definicje odpowiednich schematu.</span><span class="sxs-lookup"><span data-stu-id="1f22b-103">External mapping files and .dbml files that you modify must be validated against their respective schema definitions.</span></span> <span data-ttu-id="1f22b-104">Ten temat zawiera użytkowników programu Visual Studio czynności do wykonania procesu weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="1f22b-104">This topic provides Visual Studio users with the steps to implement the validation process.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
### <a name="to-validate-a-dbml-or-xml-file"></a><span data-ttu-id="1f22b-105">Aby sprawdzić poprawność pliku XML lub .dbml</span><span class="sxs-lookup"><span data-stu-id="1f22b-105">To validate a .dbml or XML file</span></span>  
  
1.  <span data-ttu-id="1f22b-106">W programie Visual Studio **pliku** menu wskaż **Otwórz**, a następnie kliknij przycisk **pliku**.</span><span class="sxs-lookup"><span data-stu-id="1f22b-106">On the Visual Studio **File** menu, point to **Open**, and then click **File**.</span></span>  
  
2.  <span data-ttu-id="1f22b-107">W **Otwórz plik** okna dialogowego kliknij .dbml lub plik mapowania XML, który chcesz zweryfikować.</span><span class="sxs-lookup"><span data-stu-id="1f22b-107">In the **Open File** dialog box, click the .dbml or XML mapping file that you want to validate.</span></span>  
  
     <span data-ttu-id="1f22b-108">Otwiera plik w **edytora XML**.</span><span class="sxs-lookup"><span data-stu-id="1f22b-108">The file opens in the **XML Editor**.</span></span>  
  
3.  <span data-ttu-id="1f22b-109">Kliknij prawym przyciskiem myszy okna, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="1f22b-109">Right-click the window, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="1f22b-110">W **właściwości** okna, kliknij przycisk wielokropka dla **schematy** właściwości.</span><span class="sxs-lookup"><span data-stu-id="1f22b-110">In the **Properties** window, click the ellipsis for the **Schemas** property.</span></span>  
  
     <span data-ttu-id="1f22b-111">**Schematów XML** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="1f22b-111">The **XML Schemas** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="1f22b-112">Należy zwrócić uwagę definicji schematu odpowiednie do określonych celów.</span><span class="sxs-lookup"><span data-stu-id="1f22b-112">Note the appropriate schema definition for your purpose.</span></span>  
  
    -   <span data-ttu-id="1f22b-113">DbmlSchema.xsd jest sprawdzanie poprawności pliku .dbml definicję schematu.</span><span class="sxs-lookup"><span data-stu-id="1f22b-113">DbmlSchema.xsd is the schema definition for validating a .dbml file.</span></span> <span data-ttu-id="1f22b-114">Aby uzyskać więcej informacji, zobacz [generowanie kodu w składniku LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="1f22b-114">For more information, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
    -   <span data-ttu-id="1f22b-115">LinqToSqlMapping.xsd jest definicji schematu do zweryfikowania plik mapowania XML.</span><span class="sxs-lookup"><span data-stu-id="1f22b-115">LinqToSqlMapping.xsd is the schema definition for validating an external XML mapping file.</span></span> <span data-ttu-id="1f22b-116">Aby uzyskać więcej informacji, zobacz [zewnętrznych mapowania](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="1f22b-116">For more information, see [External Mapping](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span></span>  
  
6.  <span data-ttu-id="1f22b-117">W **użyj** kolumnę żądany schemat definicji wiersza, kliknij, aby otworzyć okno listy rozwijanej, a następnie kliknij przycisk **używają tego schematu**.</span><span class="sxs-lookup"><span data-stu-id="1f22b-117">In the **Use** column of the desired schema definition row, click to open the drop-down box, and then click **Use this schema**.</span></span>  
  
     <span data-ttu-id="1f22b-118">Plik definicji schematu jest teraz skojarzone z Twojej DBML lub XML w pliku mapowania.</span><span class="sxs-lookup"><span data-stu-id="1f22b-118">The schema definition file is now associated with your DBML or XML mapping file.</span></span>  
  
     <span data-ttu-id="1f22b-119">Upewnij się, że nie wybrano żadnych definicji schematu.</span><span class="sxs-lookup"><span data-stu-id="1f22b-119">Make sure no other schema definitions are selected.</span></span>  
  
7.  <span data-ttu-id="1f22b-120">Na **widoku** menu, kliknij przycisk **listy błędów**.</span><span class="sxs-lookup"><span data-stu-id="1f22b-120">On the **View** menu, click **Error List**.</span></span>  
  
     <span data-ttu-id="1f22b-121">Ustal, czy zostały wygenerowane błędy, ostrzeżenia lub komunikaty.</span><span class="sxs-lookup"><span data-stu-id="1f22b-121">Determine whether errors, warnings, or messages have been generated.</span></span> <span data-ttu-id="1f22b-122">Jeśli nie, plik XML jest nieprawidłowa względem definicji schematu.</span><span class="sxs-lookup"><span data-stu-id="1f22b-122">If not, the XML file is valid against the schema definition.</span></span>  
  
## <a name="alternate-method-for-supplying-schema-definition"></a><span data-ttu-id="1f22b-123">Alternatywna metoda w dostarczaniu definicji schematu</span><span class="sxs-lookup"><span data-stu-id="1f22b-123">Alternate Method for Supplying Schema Definition</span></span>  
 <span data-ttu-id="1f22b-124">Jeśli zaistnieje odpowiednie XSD pliku nie ma w **schematów XML** okno dialogowe, możesz pobrać plik XSD z tematu Pomocy.</span><span class="sxs-lookup"><span data-stu-id="1f22b-124">If for some reason the appropriate .xsd file does not appear in the **XML Schemas** dialog box, you can download the .xsd file from a Help topic.</span></span> <span data-ttu-id="1f22b-125">Poniższe etapy ułatwiają Zapisz pobrany plik w formacie Unicode, wymagane edytora XML w Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1f22b-125">The following steps help you save the downloaded file in the Unicode format required by the Visual Studio XML Editor.</span></span>  
  
#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a><span data-ttu-id="1f22b-126">Aby skopiować plik definicji schematu z tematu Pomocy.</span><span class="sxs-lookup"><span data-stu-id="1f22b-126">To copy a schema definition file from a Help topic</span></span>  
  
1.  <span data-ttu-id="1f22b-127">Lokalizowanie tematu pomocy, który zawiera definicję schematu, zgodnie z opisem we wcześniejszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="1f22b-127">Locate the Help topic that contains the schema definition as described earlier in this topic.</span></span>  
  
    -   <span data-ttu-id="1f22b-128">W przypadku plików .dbml, zobacz [generowanie kodu w składniku LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="1f22b-128">For .dbml files, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
    -   <span data-ttu-id="1f22b-129">Dla zewnętrznych mapowania plików, zobacz [zewnętrznych mapowania](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="1f22b-129">For external mapping files, see [External Mapping](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span></span>  
  
2.  <span data-ttu-id="1f22b-130">Kliknij przycisk **Kopiuj kod** można skopiować pliku kodu do Schowka.</span><span class="sxs-lookup"><span data-stu-id="1f22b-130">Click **Copy Code** to copy the code file to the Clipboard.</span></span>  
  
3.  <span data-ttu-id="1f22b-131">Uruchom program Notatnik, aby utworzyć nowy plik.</span><span class="sxs-lookup"><span data-stu-id="1f22b-131">Start Notepad to create a new file.</span></span>  
  
4.  <span data-ttu-id="1f22b-132">Wklej kod ze Schowka do Notatnika.</span><span class="sxs-lookup"><span data-stu-id="1f22b-132">Paste the code from the clipboard into Notepad file.</span></span>  
  
5.  <span data-ttu-id="1f22b-133">W programie Notatnik **pliku** menu, kliknij przycisk **Zapisz jako**.</span><span class="sxs-lookup"><span data-stu-id="1f22b-133">On the Notepad **File** menu, click **Save As**.</span></span>  
  
6.  <span data-ttu-id="1f22b-134">W **kodowanie** wybierz opcję **Unicode**.</span><span class="sxs-lookup"><span data-stu-id="1f22b-134">In the **Encoding** box, select **Unicode**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="1f22b-135">Wybranie tej opcji gwarantuje, że znacznik kolejności bajtów Unicode-16 (`FFFE`) jest dołączany na początku w pliku tekstowym.</span><span class="sxs-lookup"><span data-stu-id="1f22b-135">This selection guarantees that the Unicode-16 byte-order marker (`FFFE`) is prepended to the text file.</span></span>  
  
7.  <span data-ttu-id="1f22b-136">W **nazwę pliku** Utwórz nazwę pliku z rozszerzeniem xsd.</span><span class="sxs-lookup"><span data-stu-id="1f22b-136">In the **File name** box, create a file name with an .xsd extension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f22b-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1f22b-137">See Also</span></span>  
 [<span data-ttu-id="1f22b-138">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="1f22b-138">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
