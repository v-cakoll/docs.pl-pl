---
title: 'Instrukcje: Generowanie modelu i mapowania plików za pomocą EdmGen.exe'
ms.date: 03/30/2017
ms.assetid: 40db462d-2fd2-4cc1-ad86-d280403e63fa
ms.openlocfilehash: 37234d8f0631ea11ea0d9c7d4e8f027a7266814e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958454"
---
# <a name="how-to-use-edmgenexe-to-generate-the-model-and-mapping-files"></a>Instrukcje: Generowanie modelu i mapowania plików za pomocą EdmGen.exe
W tym temacie przedstawiono sposób użycia narzędzia Generator EDM (EdmGen. exe) w celu wygenerowania następujących plików na podstawie szkolnej bazy danych:  
  
- Model koncepcyjny (plik. csdl).  
  
- Model magazynu (plik. ssdl).  
  
- Mapowanie między modelami koncepcyjnymi i magazynowymi (plik. MSL).  
  
- Kod warstwy obiektu w Visual Basic lub C#.  
  
- Wyświetl pliki.  
  
 Narzędzie EdmGen. exe używa/Mode: trybu FullGeneration do generowania plików wymienionych powyżej. Aby uzyskać więcej informacji na temat poleceń EdmGen. exe, zobacz [generator modelu EDM (EdmGen. exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).  
  
 Jeśli używasz programu EdmGen. exe do generowania modelu i plików mapowania, nadal musisz skonfigurować projekt programu Visual Studio tak, aby korzystał z programu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Aby uzyskać więcej informacji, zobacz [jak: Ręcznie skonfiguruj projekt](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))Entity Framework.  
  
> [!NOTE]
> Model koncepcyjny wygenerowany przez EdmGen. exe zawiera wszystkie obiekty w bazie danych. Jeśli chcesz wygenerować model koncepcyjny, który zawiera tylko określone obiekty, użyj Kreatora Entity Data Model. Aby uzyskać więcej informacji, zobacz [jak: Użyj kreatora](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))Entity Data Model.  
  
### <a name="to-generate-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>Aby wygenerować model szkoły dla projektu Visual Basic przy użyciu programu EdmGen. exe  
  
1. Utwórz bazę danych szkoły. Aby uzyskać więcej informacji, zobacz [Tworzenie przykładowej bazy danych szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. W wierszu polecenia wykonaj następujące polecenie bez podziałów wierszy:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:VB  
    ```  
  
### <a name="to-generate-the-school-model-for-a-c-project-using-edmgenexe"></a>Aby wygenerować model szkoły dla C# projektu przy użyciu programu EdmGen. exe  
  
1. Utwórz bazę danych szkoły. Aby uzyskać więcej informacji, zobacz [Tworzenie przykładowej bazy danych szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. W wierszu polecenia wykonaj następujące polecenie bez podziałów wierszy:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:CSharp  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Modelowanie i mapowanie](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)
- [Instrukcje: Ręcznie skonfiguruj projekt Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [Instrukcje: Wstępnie Generuj widoki, aby zwiększyć wydajność zapytań](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [Narzędzia Entity Data Model ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Instrukcje: Sprawdzanie poprawności modelu i plików mapowania przy użyciu programu EdmGen. exe](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)
