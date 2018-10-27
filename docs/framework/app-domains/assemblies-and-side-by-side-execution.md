---
title: Zestawy i wykonywanie równoczesne
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution [.NET Framework]
- assemblies [.NET Framework], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e192266aa7b98637cb05f400901f51afd3046a72
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "49415207"
---
# <a name="assemblies-and-side-by-side-execution"></a>Zestawy i wykonywanie równoczesne
Wykonanie Side-by-side jest możliwość przechowywania i wykonywania wielu wersji aplikacji lub składnika na jednym komputerze. Oznacza to, że można mieć wiele wersji środowiska uruchomieniowego i wiele wersji aplikacji i składników, które używają wersji środowiska uruchomieniowego, na tym samym komputerze, w tym samym czasie. Wykonanie Side-by-side daje większą kontrolę nad jakie wersje składnika jest powiązana aplikacja, i mieć większą kontrolę nad jakie wersje środowiska uruchomieniowego używa aplikacja.  
  
 Obsługa magazynu side-by-side i wykonywanie różnych wersji tego samego zestawu jest integralną częścią — silne nazwy i jest wbudowana w infrastrukturze środowiska uruchomieniowego. Numer wersji zestawu o silnej nazwie jest częścią swoją tożsamość, środowisko uruchomieniowe można przechowywać wiele wersji tego samego zestawu w globalnej pamięci podręcznej i ładowania tych zestawów w czasie wykonywania.  
  
 Chociaż środowisko uruchomieniowe umożliwia tworzenie aplikacji side-by-side, wykonywania side-by-side nie jest automatyczna. Aby uzyskać więcej informacji na temat tworzenia aplikacji w celu wykonania side-by-side, zobacz [wytyczne dotyczące tworzenia składników Side-by-Side Execution](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).  
  
## <a name="see-also"></a>Zobacz też  
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
- [Zestawy w środowisku uruchomieniowym CLR](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
