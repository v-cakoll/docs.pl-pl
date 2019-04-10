---
ms.openlocfilehash: 4cc91e7c6054fdb8e96cecf7120df5b9f25de56c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235576"
---
### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a>Katalogi MEF implementować interfejs IEnumerable i w związku z tym może już służyć do tworzenia serializatora

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.5, implementować interfejs IEnumerable katalogach MEF i dlatego nie będzie można utworzyć programu szeregującego (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=name> obiektu). Próba serializowania katalogu MEF powoduje zgłoszenie wyjątku.|
|Sugestia|Nie można korzystać MEF do tworzenia serializatora|
|Zakres|Duży|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
