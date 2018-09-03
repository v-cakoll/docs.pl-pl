---
title: Zarządzanie instalacjami platformy .NET Core
description: Zarządzanie wieloma wersjami programu .NET Core SDK i środowisko uruchomieniowe, na komputerze, stosowaniu strategii instalacji side-by-side.
author: leecow
ms.author: wiwagn
ms.date: 08/22/2018
ms.openlocfilehash: 06c3f43e7917efb8fd31898044d8f5d920c2cada
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43485481"
---
# <a name="manage-net-core-installations"></a>Zarządzanie instalacjami platformy .NET Core

.NET core umożliwia wielu wersji zestawu SDK i środowisko uruchomieniowe istnieje side-by-side, włączanie wersji zależności elastyczność tworzenia i uruchamiania aplikacji .NET Core. Te instalacji i zachowania przodu automatyczne wersji oferują korzyści, ale wadą Wymowa:. Jak są zainstalowane aktualizacje, środowisko uruchomieniowe programu .NET Core lub .NET Core SDK, poprzednie wersje pozostają na dysku. Wiele wersji zainstalowanej zwiększyć użycie dysku wraz z upływem czasu. Więcej niż 50 zestawu .NET Core SDK aktualizacje zostały zwolnione. Może istnieć wiele wersji zestawu SDK i środowisko uruchomieniowe zainstalowane w systemie, które mogą zostać usunięte.

## <a name="safe-to-remove"></a>Można bezpiecznie usunąć?

[Wybór wersji platformy .NET Core](selection.md) zachowań i zgodność środowiska uruchomieniowego programu .NET Core między aktualizacjami umożliwia bezpieczne usuwanie wcześniejszych wersji. Aktualizacje środowiska uruchomieniowego .NET core są zgodne w ramach wersji głównej "pasma, takich jak wersji 1.x i 2.x. Ponadto nowsze wersje programu .NET Core SDK zazwyczaj zachować możliwość tworzenia aplikacji w tym docelowymi są poprzednie wersje środowiska uruchomieniowego w sposób zgodny.

Ogólnie rzecz biorąc wystarczy tylko najnowszy zestaw SDK i najnowszą wersję poprawki środowisk uruchomieniowych wymagane dla aplikacji. Wystąpienia, gdzie przechowywanie starsze wersje zestawu SDK lub środowiska uruchomieniowego obejmują obsługi aplikacji opartych na pliku project.json.  Jeśli aplikacja ma określone przyczyny, dla starszych zestawów SDK lub środowisk wykonawczych, możesz bezpiecznie usunąć starsze wersje.

Metody usuwania platformy .NET Core różnią się od platformy i zostały zmienione nieco między wersjami .NET Core. Aby uzyskać więcej informacji na temat usuwania wersji programu .NET Core, które nie są już potrzebne, zobacz [jak usunąć środowisko uruchomieniowe programu .NET Core i zestawu SDK](remove-runtime-sdk-versions.md) w [dokumentacji platformy .NET Core](../index.md).
