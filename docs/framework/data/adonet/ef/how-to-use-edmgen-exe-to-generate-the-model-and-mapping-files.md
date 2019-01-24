---
title: 'Instrukcje: Generowanie modelu i mapowania plików za pomocą EdmGen.exe'
ms.date: 03/30/2017
ms.assetid: 40db462d-2fd2-4cc1-ad86-d280403e63fa
ms.openlocfilehash: 340ef0b20c25ca76df51085592e53849c6bf7a12
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610156"
---
# <a name="how-to-use-edmgenexe-to-generate-the-model-and-mapping-files"></a>Instrukcje: Generowanie modelu i mapowania plików za pomocą EdmGen.exe
W tym temacie przedstawiono sposób użycia narzędzia Generator EDM (EdmGen.exe), aby wygenerować następujących plików, w oparciu o bazę danych School:  
  
-   Model koncepcyjny (plik .csdl).  
  
-   Model magazynu (ssdl pliku).  
  
-   Mapowanie między modelami koncepcyjne i magazynu (pliku MSL albo identyfikatorem).  
  
-   Kod warstwy obiektu w języku Visual Basic lub C#.  
  
-   Wyświetl pliki.  
  
 Narzędzie EdmGen.exe używa /mode:FullGeneration do generowania plików wymienionych powyżej. Aby uzyskać więcej informacji na temat poleceń EdmGen.exe zobacz [Generator EDM (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).  
  
 Jeśli Generowanie modelu i mapowania plików za pomocą EdmGen.exe nadal należy skonfigurować projektu programu Visual Studio do używania [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Aby uzyskać więcej informacji, zobacz [jak: Ręczne konfigurowanie projektu programu Entity Framework](https://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e).  
  
> [!NOTE]
>  Model koncepcyjny generowane przez EdmGen.exe obejmuje wszystkie obiekty w bazie danych. Jeśli chcesz wygenerować modelu koncepcyjnego, która obejmuje tylko konkretne obiekty, należy użyć Kreator modelu Entity Data Model. Aby uzyskać więcej informacji, zobacz [jak: Użyj Kreatora modelu danych jednostki](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
### <a name="to-generate-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>Generowanie modelu szkoły w projekcie języka Visual Basic, za pomocą EdmGen.exe  
  
1.  Utwórz bazę danych School. Aby uzyskać więcej informacji, zobacz [tworzenie przykładowej bazy danych School](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).  
  
2.  W wierszu polecenia Uruchom następujące polecenie bez podziałów wiersza:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:VB  
    ```  
  
### <a name="to-generate-the-school-model-for-a-c-project-using-edmgenexe"></a>Generowanie modelu School projekt C# za pomocą EdmGen.exe  
  
1.  Utwórz bazę danych School. Aby uzyskać więcej informacji, zobacz [tworzenie przykładowej bazy danych School](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).  
  
2.  W wierszu polecenia Uruchom następujące polecenie bez podziałów wiersza:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:CSharp  
    ```  
  
## <a name="see-also"></a>Zobacz także
- [Modelowanie i mapowanie](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)
- [Instrukcje: Ręczne konfigurowanie projektu programu Entity Framework](https://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)
- [Instrukcje: Wstępnie wygenerować widoków, aby poprawić wydajność zapytań](https://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579)
- [Narzędzia do modelu danych jednostki ADO.NET](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)
- [Instrukcje: Walidacja modelu i mapowania plików za pomocą EdmGen.exe](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)
