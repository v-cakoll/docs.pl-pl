---
title: 'Instrukcje: Generowanie modelu i mapowania plików za pomocą EdmGen.exe'
ms.date: 03/30/2017
ms.assetid: 40db462d-2fd2-4cc1-ad86-d280403e63fa
ms.openlocfilehash: ee8297c0833378b2b44800355b47db9caa2dc7fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150520"
---
# <a name="how-to-use-edmgenexe-to-generate-the-model-and-mapping-files"></a>Instrukcje: Generowanie modelu i mapowania plików za pomocą EdmGen.exe
W tym temacie pokazano, jak używać narzędzia EDM Generator (EdmGen.exe) do generowania następujących plików na podstawie bazy danych szkoły:  
  
- Model koncepcyjny (plik csdl).  
  
- Model magazynu (plik .ssdl).  
  
- Mapowanie między modelami koncepcyjnymi i magazynowymi (plik msl).  
  
- Kod warstwy obiektowej w języku Visual Basic lub C#.  
  
- Wyświetlanie plików.  
  
 Narzędzie EdmGen.exe używa /mode:FullGeneration do generowania plików wymienionych powyżej. Aby uzyskać więcej informacji na temat poleceń EdmGen.exe, zobacz [Generator EDM (EdmGen.exe)](edm-generator-edmgen-exe.md).  
  
 Jeśli używasz EdmGen.exe do generowania plików modelu i mapowania, nadal trzeba skonfigurować projekt programu Visual Studio do korzystania z entity framework. Aby uzyskać więcej informacji, zobacz [Jak: Ręczne konfigurowanie projektu frameworka encji](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).  
  
> [!NOTE]
> Model koncepcyjny generowany przez program EdmGen.exe zawiera wszystkie obiekty w bazie danych. Jeśli chcesz wygenerować model koncepcyjny, który zawiera tylko określone obiekty, użyj Kreatora modelu danych jednostki. Aby uzyskać więcej informacji, zobacz [Jak: Korzystanie z Kreatora modelu danych jednostki](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
### <a name="to-generate-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>Aby wygenerować model szkoły dla projektu visual basic przy użyciu programu EdmGen.exe  
  
1. Tworzenie bazy danych Szkoły. Aby uzyskać więcej informacji, zobacz [Tworzenie przykładowej bazy danych szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. W wierszu polecenia wykonaj następujące polecenie bez podziałów wierszy:  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:VB  
    ```  
  
### <a name="to-generate-the-school-model-for-a-c-project-using-edmgenexe"></a>Aby wygenerować model szkoły dla projektu języka C# przy użyciu programu EdmGen.exe  
  
1. Tworzenie bazy danych Szkoły. Aby uzyskać więcej informacji, zobacz [Tworzenie przykładowej bazy danych szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. W wierszu polecenia wykonaj następujące polecenie bez podziałów wierszy:  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:CSharp  
    ```  
  
## <a name="see-also"></a>Zobacz też

- [Modelowanie i mapowanie](modeling-and-mapping.md)
- [Jak: Ręczne konfigurowanie projektu frameworka encji](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [Jak: Wstępnie generuj widoki, aby zwiększyć wydajność kwerendy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [Narzędzia ADO.NET modelu danych jednostki](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Instrukcje: Walidacja modelu i mapowania plików za pomocą EdmGen.exe](how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)
