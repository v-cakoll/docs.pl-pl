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
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a>Instrukcje: Używanie EdmGen.exe, aby wygenerować kod warstwy obiektu
W tym temacie przedstawiono sposób użycia narzędzia [Generator EDM (EdmGen. exe)](edm-generator-edmgen-exe.md) w celu wygenerowania kodu warstwy obiektu opartego na pliku. csdl.  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>Aby wygenerować kod warstwy obiektu dla modelu szkoły dla projektu Visual Basic przy użyciu EdmGen. exe  
  
1. Utwórz bazę danych szkoły. Aby uzyskać więcej informacji, zobacz [Tworzenie przykładowej bazy danych szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. Wygeneruj model szkoły lub uzyskaj plik uczelni. csdl. Aby uzyskać więcej informacji, zobacz [jak: Użyj programu EdmGen. exe, aby wygenerować model i pliki](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)mapowania.  
  
3. W wierszu polecenia wykonaj następujące polecenie bez podziałów wierszy:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a>Aby wygenerować kod warstwy obiektu dla modelu szkoły dla C# projektu przy użyciu EdmGen. exe  
  
1. Utwórz bazę danych szkoły. Aby uzyskać więcej informacji, zobacz [Tworzenie przykładowej bazy danych szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. Wygeneruj model szkoły lub uzyskaj plik uczelni. csdl. Aby uzyskać więcej informacji, zobacz [jak: Użyj programu EdmGen. exe, aby wygenerować model i pliki](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)mapowania.  
  
3. W wierszu polecenia wykonaj następujące polecenie bez podziałów wierszy:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Modelowanie i mapowanie](modeling-and-mapping.md)
- [Instrukcje: Ręcznie skonfiguruj projekt Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [Narzędzia Entity Data Model ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Instrukcje: Wstępnie Generuj widoki, aby zwiększyć wydajność zapytań](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [Instrukcje: Używanie programu EdmGen. exe do generowania modelu i plików mapowania](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
