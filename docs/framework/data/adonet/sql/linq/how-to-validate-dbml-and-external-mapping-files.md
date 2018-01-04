---
title: "Porady: Sprawdzanie poprawności DBML i plikami zewnętrznych mapowania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 9339176cbc6a72d940e3fa053c0e54e0667193f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a><span data-ttu-id="26e99-102">Porady: Sprawdzanie poprawności DBML i plikami zewnętrznych mapowania</span><span class="sxs-lookup"><span data-stu-id="26e99-102">How to: Validate DBML and External Mapping Files</span></span>
<span data-ttu-id="26e99-103">Mapowanie zewnętrzne pliki i pliki .dbml zmodyfikowaniu musi zostać zweryfikowany względem ich definicje odpowiednich schematu.</span><span class="sxs-lookup"><span data-stu-id="26e99-103">External mapping files and .dbml files that you modify must be validated against their respective schema definitions.</span></span> <span data-ttu-id="26e99-104">Ten temat zawiera [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] użytkownikom kroki do wykonania procesu weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="26e99-104">This topic provides [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] users with the steps to implement the validation process.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
### <a name="to-validate-a-dbml-or-xml-file"></a><span data-ttu-id="26e99-105">Aby sprawdzić poprawność pliku XML lub .dbml</span><span class="sxs-lookup"><span data-stu-id="26e99-105">To validate a .dbml or XML file</span></span>  
  
1.  <span data-ttu-id="26e99-106">W programie Visual Studio **pliku** menu wskaż **Otwórz**, a następnie kliknij przycisk **pliku**.</span><span class="sxs-lookup"><span data-stu-id="26e99-106">On the Visual Studio **File** menu, point to **Open**, and then click **File**.</span></span>  
  
2.  <span data-ttu-id="26e99-107">W **Otwórz plik** okna dialogowego kliknij .dbml lub plik mapowania XML, który chcesz zweryfikować.</span><span class="sxs-lookup"><span data-stu-id="26e99-107">In the **Open File** dialog box, click the .dbml or XML mapping file that you want to validate.</span></span>  
  
     <span data-ttu-id="26e99-108">Otwiera plik w **edytora XML**.</span><span class="sxs-lookup"><span data-stu-id="26e99-108">The file opens in the **XML Editor**.</span></span>  
  
3.  <span data-ttu-id="26e99-109">Kliknij prawym przyciskiem myszy okna, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="26e99-109">Right-click the window, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="26e99-110">W **właściwości** okna, kliknij przycisk wielokropka dla **schematy** właściwości.</span><span class="sxs-lookup"><span data-stu-id="26e99-110">In the **Properties** window, click the ellipsis for the **Schemas** property.</span></span>  
  
     <span data-ttu-id="26e99-111">**Schematów XML** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="26e99-111">The **XML Schemas** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="26e99-112">Należy zwrócić uwagę definicji schematu odpowiednie do określonych celów.</span><span class="sxs-lookup"><span data-stu-id="26e99-112">Note the appropriate schema definition for your purpose.</span></span>  
  
    -   <span data-ttu-id="26e99-113">DbmlSchema.xsd jest sprawdzanie poprawności pliku .dbml definicję schematu.</span><span class="sxs-lookup"><span data-stu-id="26e99-113">DbmlSchema.xsd is the schema definition for validating a .dbml file.</span></span> <span data-ttu-id="26e99-114">Aby uzyskać więcej informacji, zobacz [generowanie kodu w składniku LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="26e99-114">For more information, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
    -   <span data-ttu-id="26e99-115">LinqToSqlMapping.xsd jest definicji schematu do zweryfikowania plik mapowania XML.</span><span class="sxs-lookup"><span data-stu-id="26e99-115">LinqToSqlMapping.xsd is the schema definition for validating an external XML mapping file.</span></span> <span data-ttu-id="26e99-116">Aby uzyskać więcej informacji, zobacz [zewnętrznych mapowania](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="26e99-116">For more information, see [External Mapping](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span></span>  
  
6.  <span data-ttu-id="26e99-117">W **użyj** kolumnę żądany schemat definicji wiersza, kliknij, aby otworzyć okno listy rozwijanej, a następnie kliknij przycisk **używają tego schematu**.</span><span class="sxs-lookup"><span data-stu-id="26e99-117">In the **Use** column of the desired schema definition row, click to open the drop-down box, and then click **Use this schema**.</span></span>  
  
     <span data-ttu-id="26e99-118">Plik definicji schematu jest teraz skojarzone z Twojej DBML lub XML w pliku mapowania.</span><span class="sxs-lookup"><span data-stu-id="26e99-118">The schema definition file is now associated with your DBML or XML mapping file.</span></span>  
  
     <span data-ttu-id="26e99-119">Upewnij się, że nie wybrano żadnych definicji schematu.</span><span class="sxs-lookup"><span data-stu-id="26e99-119">Make sure no other schema definitions are selected.</span></span>  
  
7.  <span data-ttu-id="26e99-120">Na **widoku** menu, kliknij przycisk **listy błędów**.</span><span class="sxs-lookup"><span data-stu-id="26e99-120">On the **View** menu, click **Error List**.</span></span>  
  
     <span data-ttu-id="26e99-121">Ustal, czy zostały wygenerowane błędy, ostrzeżenia lub komunikaty.</span><span class="sxs-lookup"><span data-stu-id="26e99-121">Determine whether errors, warnings, or messages have been generated.</span></span> <span data-ttu-id="26e99-122">Jeśli nie, plik XML jest nieprawidłowa względem definicji schematu.</span><span class="sxs-lookup"><span data-stu-id="26e99-122">If not, the XML file is valid against the schema definition.</span></span>  
  
## <a name="alternate-method-for-supplying-schema-definition"></a><span data-ttu-id="26e99-123">Alternatywna metoda w dostarczaniu definicji schematu</span><span class="sxs-lookup"><span data-stu-id="26e99-123">Alternate Method for Supplying Schema Definition</span></span>  
 <span data-ttu-id="26e99-124">Jeśli zaistnieje odpowiednie XSD pliku nie ma w **schematów XML** okno dialogowe, możesz pobrać plik XSD z tematu Pomocy.</span><span class="sxs-lookup"><span data-stu-id="26e99-124">If for some reason the appropriate .xsd file does not appear in the **XML Schemas** dialog box, you can download the .xsd file from a Help topic.</span></span> <span data-ttu-id="26e99-125">Następujące kroki pomocy Zapisz pobrany plik w formacie Unicode, wymagane przez [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] edytora XML.</span><span class="sxs-lookup"><span data-stu-id="26e99-125">The following steps help you save the downloaded file in the Unicode format required by the [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] XML Editor.</span></span>  
  
#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a><span data-ttu-id="26e99-126">Aby skopiować plik definicji schematu z tematu Pomocy.</span><span class="sxs-lookup"><span data-stu-id="26e99-126">To copy a schema definition file from a Help topic</span></span>  
  
1.  <span data-ttu-id="26e99-127">Lokalizowanie tematu pomocy, który zawiera definicję schematu, zgodnie z opisem we wcześniejszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="26e99-127">Locate the Help topic that contains the schema definition as described earlier in this topic.</span></span>  
  
    -   <span data-ttu-id="26e99-128">W przypadku plików .dbml, zobacz [generowanie kodu w składniku LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="26e99-128">For .dbml files, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
    -   <span data-ttu-id="26e99-129">Dla zewnętrznych mapowania plików, zobacz [zewnętrznych mapowania](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="26e99-129">For external mapping files, see [External Mapping](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span></span>  
  
2.  <span data-ttu-id="26e99-130">Kliknij przycisk **Kopiuj kod** można skopiować pliku kodu do Schowka.</span><span class="sxs-lookup"><span data-stu-id="26e99-130">Click **Copy Code** to copy the code file to the Clipboard.</span></span>  
  
3.  <span data-ttu-id="26e99-131">Uruchom program Notatnik, aby utworzyć nowy plik.</span><span class="sxs-lookup"><span data-stu-id="26e99-131">Start Notepad to create a new file.</span></span>  
  
4.  <span data-ttu-id="26e99-132">Wklej kod ze Schowka do Notatnika.</span><span class="sxs-lookup"><span data-stu-id="26e99-132">Paste the code from the clipboard into Notepad file.</span></span>  
  
5.  <span data-ttu-id="26e99-133">W programie Notatnik **pliku** menu, kliknij przycisk **Zapisz jako**.</span><span class="sxs-lookup"><span data-stu-id="26e99-133">On the Notepad **File** menu, click **Save As**.</span></span>  
  
6.  <span data-ttu-id="26e99-134">W **kodowanie** wybierz opcję **Unicode**.</span><span class="sxs-lookup"><span data-stu-id="26e99-134">In the **Encoding** box, select **Unicode**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="26e99-135">Wybranie tej opcji gwarantuje, że znacznik kolejności bajtów Unicode-16 (`FFFE`) jest dołączany na początku w pliku tekstowym.</span><span class="sxs-lookup"><span data-stu-id="26e99-135">This selection guarantees that the Unicode-16 byte-order marker (`FFFE`) is prepended to the text file.</span></span>  
  
7.  <span data-ttu-id="26e99-136">W **nazwę pliku** Utwórz nazwę pliku z rozszerzeniem xsd.</span><span class="sxs-lookup"><span data-stu-id="26e99-136">In the **File name** box, create a file name with an .xsd extension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26e99-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="26e99-137">See Also</span></span>  
 [<span data-ttu-id="26e99-138">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="26e99-138">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
