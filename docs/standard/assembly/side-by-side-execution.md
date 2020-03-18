---
title: Zestawy i wykonywanie równoczesne
ms.date: 08/20/2019
helpviewer_keywords:
- side-by-side execution [.NET Framework]
- assemblies [.NET Framework], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
ms.openlocfilehash: 234efba66d87b520b54d6d113afcc4bba0bfe06a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138657"
---
# <a name="assemblies-and-side-by-side-execution"></a>Zestawy i wykonywanie równoczesne

Wykonanie side-by-side jest możliwość przechowywania i wykonywania wielu wersji aplikacji lub składnika na tym samym komputerze. Oznacza to, że na tym samym komputerze może być dostępnych wiele wersji programu runtime oraz wiele wersji aplikacji i składników korzystających z wersji programu runtime. Wykonanie side-by-side zapewnia większą kontrolę nad wersjami składnika, z którym aplikacja jest powiązana, oraz większą kontrolę nad wersją czasu wykonawczego używaną przez aplikację.  
  
Obsługa magazynu side-by-side i wykonywania różnych wersji tego samego zestawu jest integralną częścią silnego nazewnictwa i jest wbudowana w infrastrukturę czasu wykonawczego. Ponieważ numer wersji zestawu o silnej nazwie jest częścią jego tożsamości, w czasie wykonywania można przechowywać wiele wersji tego samego zestawu w globalnej pamięci podręcznej zestawów i załadować te zestawy w czasie wykonywania.  
  
Mimo że czas wykonywania zapewnia możliwość tworzenia aplikacji side-by-side, wykonanie side-by-side nie jest automatyczne. Aby uzyskać więcej informacji na temat tworzenia aplikacji do wykonywania obok siebie, zobacz [Wskazówki dotyczące tworzenia składników do wykonywania obok siebie](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).  
  
## <a name="see-also"></a>Zobacz też

- [Jak program runtime lokalizuje zestawy](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [Zestawy w środowisku .NET](index.md)
