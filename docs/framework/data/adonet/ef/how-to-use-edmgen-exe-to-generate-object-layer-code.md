---
title: 'Porady: Użyj EdmGen.exe, aby wygenerować kod warstwy obiektu'
ms.date: 03/30/2017
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
ms.openlocfilehash: cd919f382096af6ff3e5e27225619767f3922ff0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a>Porady: Użyj EdmGen.exe, aby wygenerować kod warstwy obiektu
W tym temacie przedstawiono sposób użycia [Generator EDM (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) narzędzie do generowania kodu warstwy obiektu oparte na pliku CSDL.  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>Aby wygenerować kod warstwy obiektu dla modelu służbowych przy użyciu EdmGen.exe projektu Visual Basic  
  
1.  Utwórz bazę danych służbowych. Aby uzyskać więcej informacji, zobacz [tworzenie przykładowej bazy danych służbowych](http://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).  
  
2.  Generowanie modelu służbowe lub pobrać plik School.csdl. Aby uzyskać więcej informacji, zobacz [porady: EdmGen.exe używany do generowania modelu i mapowania plików](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
3.  W wierszu polecenia Uruchom następujące polecenie bez podziałów wierszy:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a>Aby wygenerować kod warstwy obiektu modelu służbowe dla projektu C# za pomocą EdmGen.exe  
  
1.  Utwórz bazę danych służbowych. Aby uzyskać więcej informacji, zobacz [tworzenie przykładowej bazy danych służbowych](http://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).  
  
2.  Generowanie modelu służbowe lub pobrać plik School.csdl. Aby uzyskać więcej informacji, zobacz [porady: EdmGen.exe używany do generowania modelu i mapowania plików](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
3.  W wierszu polecenia Uruchom następujące polecenie bez podziałów wierszy:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Modelowanie i mapowanie](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)  
 [Porady: ręczne konfigurowanie projektu programu Entity Framework](http://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)  
 [ADO.NET Entity Data Model Tools](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)  
 [Porady: wstępnego wygenerowania widoków, aby poprawić wydajność zapytań](http://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579)  
 [Instrukcje: Generowanie modelu i mapowania plików za pomocą EdmGen.exe](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
