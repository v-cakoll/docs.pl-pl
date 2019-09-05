---
title: 'Instrukcje: Walidacja modelu i mapowania plików za pomocą EdmGen.exe'
ms.date: 03/30/2017
ms.assetid: 2641906a-971a-4d0b-8aee-13fabc02a1cc
ms.openlocfilehash: 4495ff3c5d55779e9db113a2a59361b643841382
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251381"
---
# <a name="how-to-use-edmgenexe-to-validate-model-and-mapping-files"></a><span data-ttu-id="6a1b0-102">Instrukcje: Walidacja modelu i mapowania plików za pomocą EdmGen.exe</span><span class="sxs-lookup"><span data-stu-id="6a1b0-102">How to: Use EdmGen.exe to Validate Model and Mapping Files</span></span>
<span data-ttu-id="6a1b0-103">W tym temacie pokazano, jak za pomocą narzędzia [Generator EDM (EdmGen. exe)](edm-generator-edmgen-exe.md) sprawdzić poprawność modelu i plików mapowania.</span><span class="sxs-lookup"><span data-stu-id="6a1b0-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md) tool to validate the model and mapping files.</span></span> <span data-ttu-id="6a1b0-104">Aby uzyskać więcej informacji, zobacz [Entity Data Model](../entity-data-model.md).</span><span class="sxs-lookup"><span data-stu-id="6a1b0-104">For more information, see [Entity Data Model](../entity-data-model.md).</span></span>  
  
### <a name="to-validate-the-school-model-using-edmgenexe"></a><span data-ttu-id="6a1b0-105">Aby sprawdzić poprawność modelu szkoły przy użyciu programu EdmGen. exe</span><span class="sxs-lookup"><span data-stu-id="6a1b0-105">To validate the School model using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="6a1b0-106">Utwórz bazę danych szkoły.</span><span class="sxs-lookup"><span data-stu-id="6a1b0-106">Create the School database.</span></span> <span data-ttu-id="6a1b0-107">Aby uzyskać więcej informacji, zobacz [Tworzenie przykładowej bazy danych szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="6a1b0-107">For more information, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="6a1b0-108">Generuj model szkoły.</span><span class="sxs-lookup"><span data-stu-id="6a1b0-108">Generate the School model.</span></span> <span data-ttu-id="6a1b0-109">Aby uzyskać więcej informacji, zobacz [jak: Użyj programu EdmGen. exe, aby wygenerować model i pliki](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)mapowania.</span><span class="sxs-lookup"><span data-stu-id="6a1b0-109">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="6a1b0-110">W wierszu polecenia wykonaj następujące polecenie bez podziałów wierszy:</span><span class="sxs-lookup"><span data-stu-id="6a1b0-110">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:ValidateArtifacts /inssdl:.\School.ssdl /inmsl:.\School.msl /incsdl:.\School.csdl  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6a1b0-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a1b0-111">See also</span></span>

- <span data-ttu-id="6a1b0-112">[Instrukcje: Ręcznie skonfiguruj projekt Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6a1b0-112">[How to: Manually Configure an Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span></span>
- <span data-ttu-id="6a1b0-113">[Narzędzia Entity Data Model ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6a1b0-113">[ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="6a1b0-114">[Instrukcje: Wstępnie Generuj widoki, aby zwiększyć wydajność zapytań](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6a1b0-114">[How to: Pre-Generate Views to Improve Query Performance](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span></span>
- [<span data-ttu-id="6a1b0-115">Instrukcje: Generowanie kodu warstwy obiektu za pomocą EdmGen. exe</span><span class="sxs-lookup"><span data-stu-id="6a1b0-115">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>](how-to-use-edmgen-exe-to-generate-object-layer-code.md)
