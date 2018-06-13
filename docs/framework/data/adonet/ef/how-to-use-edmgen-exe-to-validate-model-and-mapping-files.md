---
title: 'Porady: używanie EdmGen.exe do walidacji modelu i mapowania plików'
ms.date: 03/30/2017
ms.assetid: 2641906a-971a-4d0b-8aee-13fabc02a1cc
ms.openlocfilehash: 197af6ae86de4057b864ef211c36f19aad83b003
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755802"
---
# <a name="how-to-use-edmgenexe-to-validate-model-and-mapping-files"></a><span data-ttu-id="36283-102">Porady: używanie EdmGen.exe do walidacji modelu i mapowania plików</span><span class="sxs-lookup"><span data-stu-id="36283-102">How to: Use EdmGen.exe to Validate Model and Mapping Files</span></span>
<span data-ttu-id="36283-103">W tym temacie przedstawiono sposób użycia [Generator EDM (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) narzędzie do sprawdzania poprawności modelu i mapowania plików.</span><span class="sxs-lookup"><span data-stu-id="36283-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) tool to validate the model and mapping files.</span></span> <span data-ttu-id="36283-104">Aby uzyskać więcej informacji, zobacz [modelu Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md).</span><span class="sxs-lookup"><span data-stu-id="36283-104">For more information, see [Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md).</span></span>  
  
### <a name="to-validate-the-school-model-using-edmgenexe"></a><span data-ttu-id="36283-105">Aby sprawdzić poprawność modelu służbowych przy użyciu EdmGen.exe</span><span class="sxs-lookup"><span data-stu-id="36283-105">To validate the School model using EdmGen.exe</span></span>  
  
1.  <span data-ttu-id="36283-106">Utwórz bazę danych służbowych.</span><span class="sxs-lookup"><span data-stu-id="36283-106">Create the School database.</span></span> <span data-ttu-id="36283-107">Aby uzyskać więcej informacji, zobacz [tworzenie przykładowej bazy danych służbowych](http://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span><span class="sxs-lookup"><span data-stu-id="36283-107">For more information, see [Creating the School Sample Database](http://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span></span>  
  
2.  <span data-ttu-id="36283-108">Generowanie modelu służbowe.</span><span class="sxs-lookup"><span data-stu-id="36283-108">Generate the School model.</span></span> <span data-ttu-id="36283-109">Aby uzyskać więcej informacji, zobacz [porady: EdmGen.exe używany do generowania modelu i mapowania plików](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="36283-109">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3.  <span data-ttu-id="36283-110">W wierszu polecenia Uruchom następujące polecenie bez podziałów wierszy:</span><span class="sxs-lookup"><span data-stu-id="36283-110">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:ValidateArtifacts /inssdl:.\School.ssdl /inmsl:.\School.msl /incsdl:.\School.csdl  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="36283-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="36283-111">See Also</span></span>  
 [<span data-ttu-id="36283-112">Porady: ręczne konfigurowanie projektu programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="36283-112">How to: Manually Configure an Entity Framework Project</span></span>](http://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)  
 [<span data-ttu-id="36283-113">ADO.NET Entity Data Model Tools</span><span class="sxs-lookup"><span data-stu-id="36283-113">ADO.NET Entity Data Model  Tools</span></span>](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)  
 [<span data-ttu-id="36283-114">Porady: wstępnego wygenerowania widoków, aby poprawić wydajność zapytań</span><span class="sxs-lookup"><span data-stu-id="36283-114">How to: Pre-Generate Views to Improve Query Performance</span></span>](http://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579)  
 [<span data-ttu-id="36283-115">Instrukcje: Używanie EdmGen.exe, aby wygenerować kod warstwy obiektu</span><span class="sxs-lookup"><span data-stu-id="36283-115">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md)
