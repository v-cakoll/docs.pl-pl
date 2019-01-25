---
title: 'Instrukcje: Walidacja modelu i mapowania plików za pomocą EdmGen.exe'
ms.date: 03/30/2017
ms.assetid: 2641906a-971a-4d0b-8aee-13fabc02a1cc
ms.openlocfilehash: 87150aee8eac6a594b18b77230889c1208003dde
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566362"
---
# <a name="how-to-use-edmgenexe-to-validate-model-and-mapping-files"></a><span data-ttu-id="2f7a4-102">Instrukcje: Walidacja modelu i mapowania plików za pomocą EdmGen.exe</span><span class="sxs-lookup"><span data-stu-id="2f7a4-102">How to: Use EdmGen.exe to Validate Model and Mapping Files</span></span>
<span data-ttu-id="2f7a4-103">W tym temacie pokazano, jak używać [Generator EDM (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) narzędzie do sprawdzania poprawności modelu i mapowania plików.</span><span class="sxs-lookup"><span data-stu-id="2f7a4-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) tool to validate the model and mapping files.</span></span> <span data-ttu-id="2f7a4-104">Aby uzyskać więcej informacji, zobacz [modelu Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md).</span><span class="sxs-lookup"><span data-stu-id="2f7a4-104">For more information, see [Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md).</span></span>  
  
### <a name="to-validate-the-school-model-using-edmgenexe"></a><span data-ttu-id="2f7a4-105">Można zweryfikować modelu szkoły za pomocą EdmGen.exe</span><span class="sxs-lookup"><span data-stu-id="2f7a4-105">To validate the School model using EdmGen.exe</span></span>  
  
1.  <span data-ttu-id="2f7a4-106">Utwórz bazę danych School.</span><span class="sxs-lookup"><span data-stu-id="2f7a4-106">Create the School database.</span></span> <span data-ttu-id="2f7a4-107">Aby uzyskać więcej informacji, zobacz [tworzenie przykładowej bazy danych School](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span><span class="sxs-lookup"><span data-stu-id="2f7a4-107">For more information, see [Creating the School Sample Database](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span></span>  
  
2.  <span data-ttu-id="2f7a4-108">Generowanie modelu szkoły.</span><span class="sxs-lookup"><span data-stu-id="2f7a4-108">Generate the School model.</span></span> <span data-ttu-id="2f7a4-109">Aby uzyskać więcej informacji, zobacz [jak: Generowanie modelu i mapowania plików za pomocą EdmGen.exe](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="2f7a4-109">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3.  <span data-ttu-id="2f7a4-110">W wierszu polecenia Uruchom następujące polecenie bez podziałów wiersza:</span><span class="sxs-lookup"><span data-stu-id="2f7a4-110">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:ValidateArtifacts /inssdl:.\School.ssdl /inmsl:.\School.msl /incsdl:.\School.csdl  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2f7a4-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2f7a4-111">See also</span></span>
- [<span data-ttu-id="2f7a4-112">Instrukcje: Ręczne konfigurowanie projektu programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="2f7a4-112">How to: Manually Configure an Entity Framework Project</span></span>](https://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)
- [<span data-ttu-id="2f7a4-113">Narzędzia do modelu danych jednostki ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2f7a4-113">ADO.NET Entity Data Model  Tools</span></span>](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)
- [<span data-ttu-id="2f7a4-114">Instrukcje: Wstępnie wygenerować widoków, aby poprawić wydajność zapytań</span><span class="sxs-lookup"><span data-stu-id="2f7a4-114">How to: Pre-Generate Views to Improve Query Performance</span></span>](https://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579)
- [<span data-ttu-id="2f7a4-115">Instrukcje: Aby wygenerować kod warstwy obiektu za pomocą EdmGen.exe</span><span class="sxs-lookup"><span data-stu-id="2f7a4-115">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md)
