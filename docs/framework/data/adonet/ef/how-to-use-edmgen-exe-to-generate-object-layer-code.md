---
title: 'Instrukcje: używanie programu EdmGen. exe do generowania kodu warstwy obiektu'
ms.date: 03/30/2017
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
ms.openlocfilehash: 9182f815a502488f955f64f6c19aad7865d0c7c6
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039986"
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a><span data-ttu-id="38356-102">Instrukcje: używanie programu EdmGen. exe do generowania kodu warstwy obiektu</span><span class="sxs-lookup"><span data-stu-id="38356-102">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>
<span data-ttu-id="38356-103">W tym temacie przedstawiono sposób użycia narzędzia [Generator EDM (EdmGen. exe)](edm-generator-edmgen-exe.md) w celu wygenerowania kodu warstwy obiektu opartego na pliku. csdl.</span><span class="sxs-lookup"><span data-stu-id="38356-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md) tool to generate object-layer code  based on the .csdl file.</span></span>  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a><span data-ttu-id="38356-104">Aby wygenerować kod warstwy obiektu dla modelu szkoły dla projektu Visual Basic przy użyciu EdmGen. exe</span><span class="sxs-lookup"><span data-stu-id="38356-104">To generate object-layer code for the School model for a Visual Basic project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="38356-105">Utwórz bazę danych szkoły.</span><span class="sxs-lookup"><span data-stu-id="38356-105">Create the School database.</span></span> <span data-ttu-id="38356-106">Aby uzyskać więcej informacji, zobacz [Tworzenie przykładowej bazy danych szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="38356-106">For more information, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="38356-107">Wygeneruj model szkoły lub uzyskaj plik uczelni. csdl.</span><span class="sxs-lookup"><span data-stu-id="38356-107">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="38356-108">Aby uzyskać więcej informacji, zobacz [How to: use EdmGen. exe w celu wygenerowania modelu i plików mapowania](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="38356-108">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="38356-109">W wierszu polecenia wykonaj następujące polecenie bez podziałów wierszy:</span><span class="sxs-lookup"><span data-stu-id="38356-109">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a><span data-ttu-id="38356-110">Aby wygenerować kod warstwy obiektu dla modelu szkoły dla C# projektu przy użyciu EdmGen. exe</span><span class="sxs-lookup"><span data-stu-id="38356-110">To generate object-layer code for the School model for a C# project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="38356-111">Utwórz bazę danych szkoły.</span><span class="sxs-lookup"><span data-stu-id="38356-111">Create the School database.</span></span> <span data-ttu-id="38356-112">Aby uzyskać więcej informacji, zobacz [Tworzenie przykładowej bazy danych szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="38356-112">For more information, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="38356-113">Wygeneruj model szkoły lub uzyskaj plik uczelni. csdl.</span><span class="sxs-lookup"><span data-stu-id="38356-113">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="38356-114">Aby uzyskać więcej informacji, zobacz [How to: use EdmGen. exe w celu wygenerowania modelu i plików mapowania](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="38356-114">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="38356-115">W wierszu polecenia wykonaj następujące polecenie bez podziałów wierszy:</span><span class="sxs-lookup"><span data-stu-id="38356-115">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="38356-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38356-116">See also</span></span>

- [<span data-ttu-id="38356-117">Modelowanie i mapowanie</span><span class="sxs-lookup"><span data-stu-id="38356-117">Modeling and Mapping</span></span>](modeling-and-mapping.md)
- <span data-ttu-id="38356-118">[Instrukcje: ręczne Konfigurowanie projektu Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="38356-118">[How to: Manually Configure an Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span></span>
- <span data-ttu-id="38356-119">[Narzędzia Entity Data Model ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="38356-119">[ADO.NET Entity Data Model  Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="38356-120">[Instrukcje: wstępne Generowanie widoków w celu zwiększenia wydajności zapytań](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="38356-120">[How to: Pre-Generate Views to Improve Query Performance](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span></span>
- [<span data-ttu-id="38356-121">Instrukcje: Generowanie modelu i mapowania plików za pomocą EdmGen.exe</span><span class="sxs-lookup"><span data-stu-id="38356-121">How to: Use EdmGen.exe to Generate the Model and Mapping Files</span></span>](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
