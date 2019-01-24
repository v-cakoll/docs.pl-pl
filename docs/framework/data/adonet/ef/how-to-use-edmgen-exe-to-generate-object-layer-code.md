---
title: 'Instrukcje: Aby wygenerować kod warstwy obiektu za pomocą EdmGen.exe'
ms.date: 03/30/2017
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
ms.openlocfilehash: 63542866441cb347362e64b08b5de11bde19d50b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654571"
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a><span data-ttu-id="ed451-102">Instrukcje: Aby wygenerować kod warstwy obiektu za pomocą EdmGen.exe</span><span class="sxs-lookup"><span data-stu-id="ed451-102">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>
<span data-ttu-id="ed451-103">W tym temacie pokazano, jak używać [Generator EDM (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) narzędzia, aby wygenerować kod warstwy obiektu na podstawie .csdl pliku.</span><span class="sxs-lookup"><span data-stu-id="ed451-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) tool to generate object-layer code  based on the .csdl file.</span></span>  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a><span data-ttu-id="ed451-104">Aby wygenerować kod warstwy obiektu modelu szkoły w projekcie języka Visual Basic, za pomocą EdmGen.exe</span><span class="sxs-lookup"><span data-stu-id="ed451-104">To generate object-layer code for the School model for a Visual Basic project using EdmGen.exe</span></span>  
  
1.  <span data-ttu-id="ed451-105">Utwórz bazę danych School.</span><span class="sxs-lookup"><span data-stu-id="ed451-105">Create the School database.</span></span> <span data-ttu-id="ed451-106">Aby uzyskać więcej informacji, zobacz [tworzenie przykładowej bazy danych School](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span><span class="sxs-lookup"><span data-stu-id="ed451-106">For more information, see [Creating the School Sample Database](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span></span>  
  
2.  <span data-ttu-id="ed451-107">Generowanie modelu szkoły lub uzyskać plik School.csdl.</span><span class="sxs-lookup"><span data-stu-id="ed451-107">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="ed451-108">Aby uzyskać więcej informacji, zobacz [jak: Generowanie modelu i mapowania plików za pomocą EdmGen.exe](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="ed451-108">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3.  <span data-ttu-id="ed451-109">W wierszu polecenia Uruchom następujące polecenie bez podziałów wiersza:</span><span class="sxs-lookup"><span data-stu-id="ed451-109">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a><span data-ttu-id="ed451-110">Aby wygenerować kod warstwy obiektu modelu School projekt C# za pomocą EdmGen.exe</span><span class="sxs-lookup"><span data-stu-id="ed451-110">To generate object-layer code for the School model for a C# project using EdmGen.exe</span></span>  
  
1.  <span data-ttu-id="ed451-111">Utwórz bazę danych School.</span><span class="sxs-lookup"><span data-stu-id="ed451-111">Create the School database.</span></span> <span data-ttu-id="ed451-112">Aby uzyskać więcej informacji, zobacz [tworzenie przykładowej bazy danych School](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span><span class="sxs-lookup"><span data-stu-id="ed451-112">For more information, see [Creating the School Sample Database](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span></span>  
  
2.  <span data-ttu-id="ed451-113">Generowanie modelu szkoły lub uzyskać plik School.csdl.</span><span class="sxs-lookup"><span data-stu-id="ed451-113">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="ed451-114">Aby uzyskać więcej informacji, zobacz [jak: Generowanie modelu i mapowania plików za pomocą EdmGen.exe](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="ed451-114">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3.  <span data-ttu-id="ed451-115">W wierszu polecenia Uruchom następujące polecenie bez podziałów wiersza:</span><span class="sxs-lookup"><span data-stu-id="ed451-115">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ed451-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ed451-116">See also</span></span>
- [<span data-ttu-id="ed451-117">Modelowanie i mapowanie</span><span class="sxs-lookup"><span data-stu-id="ed451-117">Modeling and Mapping</span></span>](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)
- [<span data-ttu-id="ed451-118">Instrukcje: Ręczne konfigurowanie projektu programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="ed451-118">How to: Manually Configure an Entity Framework Project</span></span>](https://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)
- [<span data-ttu-id="ed451-119">Narzędzia do modelu danych jednostki ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ed451-119">ADO.NET Entity Data Model  Tools</span></span>](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)
- [<span data-ttu-id="ed451-120">Instrukcje: Wstępnie wygenerować widoków, aby poprawić wydajność zapytań</span><span class="sxs-lookup"><span data-stu-id="ed451-120">How to: Pre-Generate Views to Improve Query Performance</span></span>](https://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579)
- [<span data-ttu-id="ed451-121">Instrukcje: Generowanie modelu i mapowania plików za pomocą EdmGen.exe</span><span class="sxs-lookup"><span data-stu-id="ed451-121">How to: Use EdmGen.exe to Generate the Model and Mapping Files</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
