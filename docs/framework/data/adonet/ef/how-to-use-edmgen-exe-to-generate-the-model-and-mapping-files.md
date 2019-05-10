---
title: 'Instrukcje: Generowanie modelu i mapowania plików za pomocą EdmGen.exe'
ms.date: 03/30/2017
ms.assetid: 40db462d-2fd2-4cc1-ad86-d280403e63fa
ms.openlocfilehash: f5781b49817054923cbbbf4d52205b9280ea131a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64632207"
---
# <a name="how-to-use-edmgenexe-to-generate-the-model-and-mapping-files"></a>Instrukcje: Generowanie modelu i mapowania plików za pomocą EdmGen.exe
W tym temacie przedstawiono sposób użycia narzędzia Generator EDM (EdmGen.exe), aby wygenerować następujących plików, w oparciu o bazę danych School:  
  
- Model koncepcyjny (plik .csdl).  
  
- Model magazynu (ssdl pliku).  
  
- Mapowanie między modelami koncepcyjne i magazynu (pliku MSL albo identyfikatorem).  
  
- Kod warstwy obiektu w języku Visual Basic lub C#.  
  
- Wyświetl pliki.  
  
 Narzędzie EdmGen.exe używa /mode:FullGeneration do generowania plików wymienionych powyżej. Aby uzyskać więcej informacji na temat poleceń EdmGen.exe zobacz [Generator EDM (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).  
  
 Jeśli Generowanie modelu i mapowania plików za pomocą EdmGen.exe nadal należy skonfigurować projektu programu Visual Studio do używania [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Aby uzyskać więcej informacji, zobacz [jak: Ręczne konfigurowanie projektu programu Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).  
  
> [!NOTE]
>  Model koncepcyjny generowane przez EdmGen.exe obejmuje wszystkie obiekty w bazie danych. Jeśli chcesz wygenerować modelu koncepcyjnego, która obejmuje tylko konkretne obiekty, należy użyć Kreator modelu Entity Data Model. Aby uzyskać więcej informacji, zobacz [jak: Użyj Kreatora modelu danych jednostki](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
### <a name="to-generate-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>Generowanie modelu szkoły w projekcie języka Visual Basic, za pomocą EdmGen.exe  
  
1. Utwórz bazę danych School. Aby uzyskać więcej informacji, zobacz [tworzenie przykładowej bazy danych School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. W wierszu polecenia Uruchom następujące polecenie bez podziałów wiersza:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:VB  
    ```  
  
### <a name="to-generate-the-school-model-for-a-c-project-using-edmgenexe"></a>Generowanie modelu School projekt C# za pomocą EdmGen.exe  
  
1. Utwórz bazę danych School. Aby uzyskać więcej informacji, zobacz [tworzenie przykładowej bazy danych School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. W wierszu polecenia Uruchom następujące polecenie bez podziałów wiersza:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:CSharp  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Modelowanie i mapowanie](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)
- [Instrukcje: Ręczne konfigurowanie projektu programu Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [Instrukcje: Wstępnie wygenerować widoków, aby poprawić wydajność zapytań](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [Narzędzia do modelu danych jednostki ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Instrukcje: Walidacja modelu i mapowania plików za pomocą EdmGen.exe](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)
