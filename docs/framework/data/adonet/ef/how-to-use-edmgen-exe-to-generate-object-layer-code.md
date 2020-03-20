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
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a>Instrukcje: Używanie EdmGen.exe, aby wygenerować kod warstwy obiektu
W tym temacie pokazano, jak używać narzędzia [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md) do generowania kodu warstwy obiektowej na podstawie pliku csdl.  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>Aby wygenerować kod warstwy obiektowej dla modelu szkoły dla projektu języka Visual Basic przy użyciu programu EdmGen.exe  
  
1. Tworzenie bazy danych Szkoły. Aby uzyskać więcej informacji, zobacz [Tworzenie przykładowej bazy danych szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. Wygeneruj model Szkoły lub uzyskaj plik School.csdl. Aby uzyskać więcej informacji, zobacz [Jak: Generowanie plików modelu i mapowania za pomocą programu EdmGen.exe](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
3. W wierszu polecenia wykonaj następujące polecenie bez podziałów wierszy:  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a>Aby wygenerować kod warstwy obiektowej dla modelu szkoły dla projektu C# przy użyciu programu EdmGen.exe  
  
1. Tworzenie bazy danych Szkoły. Aby uzyskać więcej informacji, zobacz [Tworzenie przykładowej bazy danych szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. Wygeneruj model Szkoły lub uzyskaj plik School.csdl. Aby uzyskać więcej informacji, zobacz [Jak: Generowanie plików modelu i mapowania za pomocą programu EdmGen.exe](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
3. W wierszu polecenia wykonaj następujące polecenie bez podziałów wierszy:  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a>Zobacz też

- [Modelowanie i mapowanie](modeling-and-mapping.md)
- [Jak: Ręczne konfigurowanie projektu frameworka encji](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [Narzędzia ADO.NET modelu danych jednostki](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Jak: Wstępnie generuj widoki, aby zwiększyć wydajność kwerendy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [Instrukcje: Generowanie modelu i mapowania plików za pomocą EdmGen.exe](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
