---
title: Plik określony w nazwie pliku nie jest prawidłowym plikiem XML
ms.date: 07/20/2015
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
ms.openlocfilehash: 3aecb0c2c87539717656a29f5b48f94fce3c8453
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43481879"
---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a><span data-ttu-id="a74cc-102">Plik określony w nazwie pliku nie jest prawidłowym plikiem XML</span><span class="sxs-lookup"><span data-stu-id="a74cc-102">File specified in FileName is not a valid XML file</span></span>
<span data-ttu-id="a74cc-103">Podanej nazwy pliku nie jest prawidłowym plikiem XML.</span><span class="sxs-lookup"><span data-stu-id="a74cc-103">The file name that you supplied is not a valid XML file.</span></span> <span data-ttu-id="a74cc-104">Aby określić dozwolone struktury i zawartości dokumentu XML, można użyć definicji typu dokumentu (DTD), schemat Microsoft-danych XML (XDR) lub schematu języka (XSD) definicji schematu XML.</span><span class="sxs-lookup"><span data-stu-id="a74cc-104">To specify the allowed structure and content of an XML document, you can use a Document Type Definition (DTD), a Microsoft XML-Data Reduced (XDR) schema, or an XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="a74cc-105">Schematy XSD są preferowanym sposobem określenia gramatyki XML w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a74cc-105">XSD schemas are the preferred way to specify XML grammars in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a74cc-106">W niektórych starszych wersjach programu Visual Studio **Projektant XML** jest Projektant typizowanych zestawów danych i schematu XML.</span><span class="sxs-lookup"><span data-stu-id="a74cc-106">In some earlier versions of Visual Studio, the **XML Designer** is the designer for typed datasets and XML schema.</span></span> <span data-ttu-id="a74cc-107">**Projektant XML** nadal można tworzyć i edytować pliki schematów XML.</span><span class="sxs-lookup"><span data-stu-id="a74cc-107">The **XML Designer** can still be used to create and edit XML schema files.</span></span> <span data-ttu-id="a74cc-108">Jednak w [!INCLUDE[vs_current_long](~/includes/vs-current-long-md.md)], Projektant do tworzenia i edytowania zestawów **Projektanta obiektów Dataset**.</span><span class="sxs-lookup"><span data-stu-id="a74cc-108">However, in [!INCLUDE[vs_current_long](~/includes/vs-current-long-md.md)], the designer for creating and editing typed datasets is the **Dataset Designer**.</span></span> <span data-ttu-id="a74cc-109">Aby uzyskać więcej informacji, zobacz [tworzenie i edytowanie wpisanych zestawów danych](/visualstudio/data-tools/creating-and-editing-typed-datasets).</span><span class="sxs-lookup"><span data-stu-id="a74cc-109">For more information, see [Creating and Editing Typed Datasets](/visualstudio/data-tools/creating-and-editing-typed-datasets).</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a74cc-110">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="a74cc-110">To correct this error</span></span>  
  
-   <span data-ttu-id="a74cc-111">Sprawdź, czy są podawania poprawnej nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="a74cc-111">Check that you are supplying the correct file name.</span></span>  
  
-   <span data-ttu-id="a74cc-112">Sprawdź, czy określony plik zawiera prawidłowy kod XML, ładując plik XML, który chcesz zaewidencjonować w **Projektant XML**.</span><span class="sxs-lookup"><span data-stu-id="a74cc-112">Check that the specified file contains valid XML by loading the XML file that you want to check into the **XML Designer**.</span></span> <span data-ttu-id="a74cc-113">Z **XML** menu, kliknij przycisk **sprawdzania poprawności XML**.</span><span class="sxs-lookup"><span data-stu-id="a74cc-113">From the **XML** menu, click **Validate XML**.</span></span> <span data-ttu-id="a74cc-114">Błędy są wyświetlane w **listy zadań**.</span><span class="sxs-lookup"><span data-stu-id="a74cc-114">Errors are displayed in the **Task List**.</span></span>  
  
-   <span data-ttu-id="a74cc-115">Jeśli plik XML ma skojarzonego schematu XML, sprawdź, czy elementy są wyświetlane w zdefiniowanej strukturze i że zawartość poszczególnych elementów zgodne typy danych zadeklarowany, określona w schemacie.</span><span class="sxs-lookup"><span data-stu-id="a74cc-115">If the XML file has an associated XML Schema, check that the elements appear in the defined structure and that the content of the individual elements conforms to the declared data types specified in the schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a74cc-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a74cc-116">See Also</span></span>  
 <xref:System.Xml>  
 [<span data-ttu-id="a74cc-117">Instrukcje: analizowanie ścieżek plików</span><span class="sxs-lookup"><span data-stu-id="a74cc-117">How to: Parse File Paths</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
