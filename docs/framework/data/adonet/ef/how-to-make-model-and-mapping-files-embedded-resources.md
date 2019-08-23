---
title: 'Instrukcje: Marka, model i mapowanie plików zasobów osadzonych'
ms.date: 03/30/2017
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
ms.openlocfilehash: 53817498f6d772c308888c5e994fb25239c4ed61
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949744"
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a>Instrukcje: Marka, model i mapowanie plików zasobów osadzonych
[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Umożliwia wdrażanie modelu i plików mapowania jako zasobów osadzonych aplikacji. Zestaw z osadzonym modelem i plikami mapowania musi być załadowany w tej samej domenie aplikacji co połączenie jednostki. Aby uzyskać więcej informacji, zobacz [Parametry połączenia](../../../../../docs/framework/data/adonet/ef/connection-strings.md). Domyślnie narzędzia Entity Data Model osadzają model i pliki mapowania. Podczas ręcznego definiowania modelu i plików mapowania Użyj tej procedury, aby upewnić się, że pliki są wdrażane jako zasoby osadzone razem z [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikacją.  
  
> [!NOTE]
> Aby zapewnić obsługę zasobów osadzonych, należy powtórzyć tę procedurę przy każdej modyfikacji modelu i plików mapowania.  
  
### <a name="to-embed-model-and-mapping-files"></a>Aby osadzić model i pliki mapowania  
  
1. W **Eksplorator rozwiązań**wybierz plik koncepcyjny (. csdl).  
  
2. W okienku **Właściwości** ustaw opcję **Akcja kompilacji** na **zasób osadzony**.  
  
3. Powtórz kroki 1 i 2 dla pliku Storage (. ssdl) i pliku mapowania (. MSL).  
  
4. W **Eksplorator rozwiązań**kliknij dwukrotnie plik App. config, a następnie zmodyfikuj `Metadata` parametr w `connectionString` atrybucie na podstawie jednego z następujących formatów:  
  
    - `Metadata=``res://<assemblyFullName>/<resourceName>;`  
  
    - `Metadata=``res://*/<resourceName>;`  
  
    - `Metadata=res://*;`  
  
     Aby uzyskać więcej informacji, zobacz [Parametry połączenia](../../../../../docs/framework/data/adonet/ef/connection-strings.md).  
  
## <a name="example"></a>Przykład  
 Poniższe parametry połączenia odwołują się do osadzonego modelu i plików mapowania dla [modelu sprzedaży AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks). Te parametry połączenia są przechowywane w pliku App. config projektu.  

## <a name="see-also"></a>Zobacz także

- [Modelowanie i mapowanie](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)
- [Instrukcje: Definiowanie parametrów połączenia](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md)
- [Instrukcje: Tworzenie parametrów połączenia usługi EntityConnection](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)
- [Narzędzia Entity Data Model ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
