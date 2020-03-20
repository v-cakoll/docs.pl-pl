---
title: 'Instrukcje: Używanie EdmGen.exe, aby wygenerować kod warstwy obiektu'
ms.date: 03/30/2017
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
ms.openlocfilehash: 1dbd2e25d5f9795af4f80e079c6a0b807666743d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150561"
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a><span data-ttu-id="07ea3-102">Instrukcje: Używanie EdmGen.exe, aby wygenerować kod warstwy obiektu</span><span class="sxs-lookup"><span data-stu-id="07ea3-102">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>
<span data-ttu-id="07ea3-103">W tym temacie pokazano, jak używać narzędzia [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md) do generowania kodu warstwy obiektowej na podstawie pliku csdl.</span><span class="sxs-lookup"><span data-stu-id="07ea3-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md) tool to generate object-layer code  based on the .csdl file.</span></span>  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a><span data-ttu-id="07ea3-104">Aby wygenerować kod warstwy obiektowej dla modelu szkoły dla projektu języka Visual Basic przy użyciu programu EdmGen.exe</span><span class="sxs-lookup"><span data-stu-id="07ea3-104">To generate object-layer code for the School model for a Visual Basic project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="07ea3-105">Tworzenie bazy danych Szkoły.</span><span class="sxs-lookup"><span data-stu-id="07ea3-105">Create the School database.</span></span> <span data-ttu-id="07ea3-106">Aby uzyskać więcej informacji, zobacz [Tworzenie przykładowej bazy danych szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="07ea3-106">For more information, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="07ea3-107">Wygeneruj model Szkoły lub uzyskaj plik School.csdl.</span><span class="sxs-lookup"><span data-stu-id="07ea3-107">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="07ea3-108">Aby uzyskać więcej informacji, zobacz [Jak: Generowanie plików modelu i mapowania za pomocą programu EdmGen.exe](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="07ea3-108">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="07ea3-109">W wierszu polecenia wykonaj następujące polecenie bez podziałów wierszy:</span><span class="sxs-lookup"><span data-stu-id="07ea3-109">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a><span data-ttu-id="07ea3-110">Aby wygenerować kod warstwy obiektowej dla modelu szkoły dla projektu C# przy użyciu programu EdmGen.exe</span><span class="sxs-lookup"><span data-stu-id="07ea3-110">To generate object-layer code for the School model for a C# project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="07ea3-111">Tworzenie bazy danych Szkoły.</span><span class="sxs-lookup"><span data-stu-id="07ea3-111">Create the School database.</span></span> <span data-ttu-id="07ea3-112">Aby uzyskać więcej informacji, zobacz [Tworzenie przykładowej bazy danych szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="07ea3-112">For more information, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="07ea3-113">Wygeneruj model Szkoły lub uzyskaj plik School.csdl.</span><span class="sxs-lookup"><span data-stu-id="07ea3-113">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="07ea3-114">Aby uzyskać więcej informacji, zobacz [Jak: Generowanie plików modelu i mapowania za pomocą programu EdmGen.exe](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="07ea3-114">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="07ea3-115">W wierszu polecenia wykonaj następujące polecenie bez podziałów wierszy:</span><span class="sxs-lookup"><span data-stu-id="07ea3-115">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="07ea3-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="07ea3-116">See also</span></span>

- [<span data-ttu-id="07ea3-117">Modelowanie i mapowanie</span><span class="sxs-lookup"><span data-stu-id="07ea3-117">Modeling and Mapping</span></span>](modeling-and-mapping.md)
- <span data-ttu-id="07ea3-118">[Jak: Ręczne konfigurowanie projektu frameworka encji](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="07ea3-118">[How to: Manually Configure an Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span></span>
- <span data-ttu-id="07ea3-119">[Narzędzia ADO.NET modelu danych jednostki](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="07ea3-119">[ADO.NET Entity Data Model  Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="07ea3-120">[Jak: Wstępnie generuj widoki, aby zwiększyć wydajność kwerendy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="07ea3-120">[How to: Pre-Generate Views to Improve Query Performance](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span></span>
- [<span data-ttu-id="07ea3-121">Instrukcje: Generowanie modelu i mapowania plików za pomocą EdmGen.exe</span><span class="sxs-lookup"><span data-stu-id="07ea3-121">How to: Use EdmGen.exe to Generate the Model and Mapping Files</span></span>](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
