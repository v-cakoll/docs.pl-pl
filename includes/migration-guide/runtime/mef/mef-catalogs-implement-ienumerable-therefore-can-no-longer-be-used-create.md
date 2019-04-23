---
ms.openlocfilehash: 4cc91e7c6054fdb8e96cecf7120df5b9f25de56c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804773"
---
### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a>Katalogi MEF implementować interfejs IEnumerable i w związku z tym może już służyć do tworzenia serializatora

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.5, implementować interfejs IEnumerable katalogach MEF i dlatego nie będzie można utworzyć programu szeregującego (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=name> obiektu). Próba serializowania katalogu MEF powoduje zgłoszenie wyjątku.|
|Sugestia|Nie można korzystać MEF do tworzenia serializatora|
|Zakres|Duży|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
