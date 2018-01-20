---
title: "Porady: używanie EdmGen.exe do walidacji modelu i mapowania plików"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2641906a-971a-4d0b-8aee-13fabc02a1cc
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: ae70c90fc20265334cdfb55e4a0f88724284d822
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-use-edmgenexe-to-validate-model-and-mapping-files"></a>Porady: używanie EdmGen.exe do walidacji modelu i mapowania plików
W tym temacie przedstawiono sposób użycia [Generator EDM (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) narzędzie do sprawdzania poprawności modelu i mapowania plików. Aby uzyskać więcej informacji, zobacz [modelu Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md).  
  
### <a name="to-validate-the-school-model-using-edmgenexe"></a>Aby sprawdzić poprawność modelu służbowych przy użyciu EdmGen.exe  
  
1.  Utwórz bazę danych służbowych. Aby uzyskać więcej informacji, zobacz [tworzenie przykładowej bazy danych służbowych](http://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).  
  
2.  Generowanie modelu służbowe. Aby uzyskać więcej informacji, zobacz [porady: EdmGen.exe używany do generowania modelu i mapowania plików](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
3.  W wierszu polecenia Uruchom następujące polecenie bez podziałów wierszy:  
  
    ```console
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:ValidateArtifacts /inssdl:.\School.ssdl /inmsl:.\School.msl /incsdl:.\School.csdl  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: ręczne konfigurowanie projektu programu Entity Framework](http://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)  
 [ADO.NET Entity Data Model Tools](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)  
 [Porady: wstępnego wygenerowania widoków, aby poprawić wydajność zapytań](http://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579)  
 [Instrukcje: Używanie EdmGen.exe, aby wygenerować kod warstwy obiektu](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md)
