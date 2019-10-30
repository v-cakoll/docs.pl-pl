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
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a>Instrukcje: używanie programu EdmGen. exe do generowania kodu warstwy obiektu
W tym temacie przedstawiono sposób użycia narzędzia [Generator EDM (EdmGen. exe)](edm-generator-edmgen-exe.md) w celu wygenerowania kodu warstwy obiektu opartego na pliku. csdl.  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>Aby wygenerować kod warstwy obiektu dla modelu szkoły dla projektu Visual Basic przy użyciu EdmGen. exe  
  
1. Utwórz bazę danych szkoły. Aby uzyskać więcej informacji, zobacz [Tworzenie przykładowej bazy danych szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. Wygeneruj model szkoły lub uzyskaj plik uczelni. csdl. Aby uzyskać więcej informacji, zobacz [How to: use EdmGen. exe w celu wygenerowania modelu i plików mapowania](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
3. W wierszu polecenia wykonaj następujące polecenie bez podziałów wierszy:  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a>Aby wygenerować kod warstwy obiektu dla modelu szkoły dla C# projektu przy użyciu EdmGen. exe  
  
1. Utwórz bazę danych szkoły. Aby uzyskać więcej informacji, zobacz [Tworzenie przykładowej bazy danych szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. Wygeneruj model szkoły lub uzyskaj plik uczelni. csdl. Aby uzyskać więcej informacji, zobacz [How to: use EdmGen. exe w celu wygenerowania modelu i plików mapowania](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
3. W wierszu polecenia wykonaj następujące polecenie bez podziałów wierszy:  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Modelowanie i mapowanie](modeling-and-mapping.md)
- [Instrukcje: ręczne Konfigurowanie projektu Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [Narzędzia Entity Data Model ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Instrukcje: wstępne Generowanie widoków w celu zwiększenia wydajności zapytań](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [Instrukcje: Generowanie modelu i mapowania plików za pomocą EdmGen.exe](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
