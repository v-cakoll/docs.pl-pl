---
title: 'Instrukcje: Używanie EdmGen.exe, aby wygenerować kod warstwy obiektu'
ms.date: 03/30/2017
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
ms.openlocfilehash: b85bacff093c268cd35dca2ede36e6ceb74ca4d1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251407"
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a><span data-ttu-id="d76a0-102">Instrukcje: Używanie EdmGen.exe, aby wygenerować kod warstwy obiektu</span><span class="sxs-lookup"><span data-stu-id="d76a0-102">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>
<span data-ttu-id="d76a0-103">W tym temacie przedstawiono sposób użycia narzędzia [Generator EDM (EdmGen. exe)](edm-generator-edmgen-exe.md) w celu wygenerowania kodu warstwy obiektu opartego na pliku. csdl.</span><span class="sxs-lookup"><span data-stu-id="d76a0-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md) tool to generate object-layer code  based on the .csdl file.</span></span>  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a><span data-ttu-id="d76a0-104">Aby wygenerować kod warstwy obiektu dla modelu szkoły dla projektu Visual Basic przy użyciu EdmGen. exe</span><span class="sxs-lookup"><span data-stu-id="d76a0-104">To generate object-layer code for the School model for a Visual Basic project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="d76a0-105">Utwórz bazę danych szkoły.</span><span class="sxs-lookup"><span data-stu-id="d76a0-105">Create the School database.</span></span> <span data-ttu-id="d76a0-106">Aby uzyskać więcej informacji, zobacz [Tworzenie przykładowej bazy danych szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d76a0-106">For more information, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="d76a0-107">Wygeneruj model szkoły lub uzyskaj plik uczelni. csdl.</span><span class="sxs-lookup"><span data-stu-id="d76a0-107">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="d76a0-108">Aby uzyskać więcej informacji, zobacz [jak: Użyj programu EdmGen. exe, aby wygenerować model i pliki](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)mapowania.</span><span class="sxs-lookup"><span data-stu-id="d76a0-108">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="d76a0-109">W wierszu polecenia wykonaj następujące polecenie bez podziałów wierszy:</span><span class="sxs-lookup"><span data-stu-id="d76a0-109">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a><span data-ttu-id="d76a0-110">Aby wygenerować kod warstwy obiektu dla modelu szkoły dla C# projektu przy użyciu EdmGen. exe</span><span class="sxs-lookup"><span data-stu-id="d76a0-110">To generate object-layer code for the School model for a C# project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="d76a0-111">Utwórz bazę danych szkoły.</span><span class="sxs-lookup"><span data-stu-id="d76a0-111">Create the School database.</span></span> <span data-ttu-id="d76a0-112">Aby uzyskać więcej informacji, zobacz [Tworzenie przykładowej bazy danych szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d76a0-112">For more information, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="d76a0-113">Wygeneruj model szkoły lub uzyskaj plik uczelni. csdl.</span><span class="sxs-lookup"><span data-stu-id="d76a0-113">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="d76a0-114">Aby uzyskać więcej informacji, zobacz [jak: Użyj programu EdmGen. exe, aby wygenerować model i pliki](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)mapowania.</span><span class="sxs-lookup"><span data-stu-id="d76a0-114">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="d76a0-115">W wierszu polecenia wykonaj następujące polecenie bez podziałów wierszy:</span><span class="sxs-lookup"><span data-stu-id="d76a0-115">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d76a0-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d76a0-116">See also</span></span>

- [<span data-ttu-id="d76a0-117">Modelowanie i mapowanie</span><span class="sxs-lookup"><span data-stu-id="d76a0-117">Modeling and Mapping</span></span>](modeling-and-mapping.md)
- <span data-ttu-id="d76a0-118">[Instrukcje: Ręcznie skonfiguruj projekt Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d76a0-118">[How to: Manually Configure an Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span></span>
- <span data-ttu-id="d76a0-119">[Narzędzia Entity Data Model ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d76a0-119">[ADO.NET Entity Data Model  Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="d76a0-120">[Instrukcje: Wstępnie Generuj widoki, aby zwiększyć wydajność zapytań](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d76a0-120">[How to: Pre-Generate Views to Improve Query Performance](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span></span>
- [<span data-ttu-id="d76a0-121">Instrukcje: Używanie programu EdmGen. exe do generowania modelu i plików mapowania</span><span class="sxs-lookup"><span data-stu-id="d76a0-121">How to: Use EdmGen.exe to Generate the Model and Mapping Files</span></span>](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
