---
title: 'Instrukcje: Marka, model i mapowanie plików zasobów osadzonych'
ms.date: 03/30/2017
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
ms.openlocfilehash: 371f8f0317295ee39d543b5637afb93102036b62
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854592"
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a>Instrukcje: Marka, model i mapowanie plików zasobów osadzonych
Entity Framework umożliwia wdrażanie modelu i plików mapowania jako zasobów osadzonych aplikacji. Zestaw z osadzonym modelem i plikami mapowania musi być załadowany w tej samej domenie aplikacji co połączenie jednostki. Aby uzyskać więcej informacji, zobacz [Parametry połączenia](connection-strings.md). Domyślnie narzędzia Entity Data Model osadzają model i pliki mapowania. Podczas ręcznego definiowania modelu i plików mapowania Użyj tej procedury, aby upewnić się, że pliki są wdrażane jako zasoby osadzone razem z aplikacją Entity Framework.  
  
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
  
     Aby uzyskać więcej informacji, zobacz [Parametry połączenia](connection-strings.md).  
  
## <a name="example"></a>Przykład  
 Poniższe parametry połączenia odwołują się do osadzonego modelu i plików mapowania dla [modelu sprzedaży AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks). Te parametry połączenia są przechowywane w pliku App. config projektu.  

## <a name="see-also"></a>Zobacz także

- [Modelowanie i mapowanie](modeling-and-mapping.md)
- [Instrukcje: Definiowanie parametrów połączenia](how-to-define-the-connection-string.md)
- [Instrukcje: Tworzenie parametrów połączenia usługi EntityConnection](how-to-build-an-entityconnection-connection-string.md)
- [Narzędzia Entity Data Model ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
