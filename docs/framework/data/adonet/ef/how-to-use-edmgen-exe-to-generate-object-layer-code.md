---
title: 'Instrukcje: Używanie EdmGen.exe, aby wygenerować kod warstwy obiektu'
ms.date: 03/30/2017
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
ms.openlocfilehash: 8a39027ee6a5647bbd645f5a38e35d61f7ebbd8e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61605772"
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a><span data-ttu-id="c5490-102">Instrukcje: Używanie EdmGen.exe, aby wygenerować kod warstwy obiektu</span><span class="sxs-lookup"><span data-stu-id="c5490-102">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>
<span data-ttu-id="c5490-103">W tym temacie pokazano, jak używać [Generator EDM (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) narzędzia, aby wygenerować kod warstwy obiektu na podstawie .csdl pliku.</span><span class="sxs-lookup"><span data-stu-id="c5490-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) tool to generate object-layer code  based on the .csdl file.</span></span>  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a><span data-ttu-id="c5490-104">Aby wygenerować kod warstwy obiektu modelu szkoły w projekcie języka Visual Basic, za pomocą EdmGen.exe</span><span class="sxs-lookup"><span data-stu-id="c5490-104">To generate object-layer code for the School model for a Visual Basic project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="c5490-105">Utwórz bazę danych School.</span><span class="sxs-lookup"><span data-stu-id="c5490-105">Create the School database.</span></span> <span data-ttu-id="c5490-106">Aby uzyskać więcej informacji, zobacz [tworzenie przykładowej bazy danych School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="c5490-106">For more information, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="c5490-107">Generowanie modelu szkoły lub uzyskać plik School.csdl.</span><span class="sxs-lookup"><span data-stu-id="c5490-107">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="c5490-108">Aby uzyskać więcej informacji, zobacz [jak: Generowanie modelu i mapowania plików za pomocą EdmGen.exe](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="c5490-108">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="c5490-109">W wierszu polecenia Uruchom następujące polecenie bez podziałów wiersza:</span><span class="sxs-lookup"><span data-stu-id="c5490-109">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a><span data-ttu-id="c5490-110">Aby wygenerować kod warstwy obiektu modelu School projekt C# za pomocą EdmGen.exe</span><span class="sxs-lookup"><span data-stu-id="c5490-110">To generate object-layer code for the School model for a C# project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="c5490-111">Utwórz bazę danych School.</span><span class="sxs-lookup"><span data-stu-id="c5490-111">Create the School database.</span></span> <span data-ttu-id="c5490-112">Aby uzyskać więcej informacji, zobacz [tworzenie przykładowej bazy danych School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="c5490-112">For more information, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="c5490-113">Generowanie modelu szkoły lub uzyskać plik School.csdl.</span><span class="sxs-lookup"><span data-stu-id="c5490-113">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="c5490-114">Aby uzyskać więcej informacji, zobacz [jak: Generowanie modelu i mapowania plików za pomocą EdmGen.exe](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="c5490-114">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="c5490-115">W wierszu polecenia Uruchom następujące polecenie bez podziałów wiersza:</span><span class="sxs-lookup"><span data-stu-id="c5490-115">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c5490-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5490-116">See also</span></span>

- [<span data-ttu-id="c5490-117">Modelowanie i mapowanie</span><span class="sxs-lookup"><span data-stu-id="c5490-117">Modeling and Mapping</span></span>](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)
- <span data-ttu-id="c5490-118">[Instrukcje: Ręczne konfigurowanie projektu programu Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c5490-118">[How to: Manually Configure an Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span></span>
- <span data-ttu-id="c5490-119">[Narzędzia do modelu danych jednostki ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c5490-119">[ADO.NET Entity Data Model  Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="c5490-120">[Instrukcje: Wstępnie wygenerować widoków, aby poprawić wydajność zapytań](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c5490-120">[How to: Pre-Generate Views to Improve Query Performance](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span></span>
- [<span data-ttu-id="c5490-121">Instrukcje: Generowanie modelu i mapowania plików za pomocą EdmGen.exe</span><span class="sxs-lookup"><span data-stu-id="c5490-121">How to: Use EdmGen.exe to Generate the Model and Mapping Files</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
