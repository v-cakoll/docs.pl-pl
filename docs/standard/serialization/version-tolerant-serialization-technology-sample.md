---
title: Przykład technologii serializacji z tolerancją wersji
ms.date: 03/30/2017
ms.assetid: 2a183664-bfbf-4ff0-96f6-c836284ea916
ms.openlocfilehash: 317a47d46b839417e01eed9deca2459a96aaa201
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960776"
---
# <a name="version-tolerant-serialization-technology-sample"></a>Przykład technologii serializacji z tolerancją wersji
[Pobierz przykład](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/VTS.zip.exe)  
  
 Ten przykład ilustruje funkcję tolerancji wersji serializacji platformy .NET. Przykład tworzy aplikacje, które używają różnych wersji programu, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> do serializacji i deserializacji danych. Mimo obecności różnych wersji typu, aplikacje komunikują się bezproblemowo. Aby uzyskać więcej informacji, zobacz [Serializacja odporna na wersje](../../../docs/standard/serialization/version-tolerant-serialization.md).  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a>Aby skompilować przykład za pomocą wiersza polecenia  
  
1. Otwórz okno wiersza polecenia i przejdź do jednego z podkatalogów specyficznych dla języka (w aplikacji v1 lub v2) dla przykładu.  
  
2. Wpisz **MSBuild. exe \<Ver> Application. sln** w wierszu polecenia (gdzie \<Ver> ma wartość v1 lub v2).  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Aby skompilować przykład za pomocą programu Visual Studio  
  
1. Otwórz Eksploratora plików i przejdź do jednego z podkatalogów właściwych dla języka dla przykładu.  
  
2. Przejdź do podkatalogu aplikacji w wersji 1 katalogu, który został wybrany w poprzednim kroku.  
  
3. Kliknij dwukrotnie ikonę aplikacji v1. sln, aby otworzyć plik w programie Visual Studio.  
  
4. W menu **Kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.  
  
5. Przejdź do podkatalogu aplikacji w wersji 2 i Powtórz dwa poprzednie kroki w celu skompilowania aplikacji w wersji 2.  
  
 Aplikacje zostaną skompilowane w domyślnych podkatalogach \Bin lub \bin\Debug odpowiednich katalogów projektu.  
  
### <a name="to-run-the-sample"></a>Aby uruchomić przykład  
  
1. W oknie wiersza polecenia przejdź do podkatalogu specyficznego dla języka, który został wybrany podczas tworzenia przykładowych aplikacji.  
  
2. Wpisz **RUNME. cmd** w wierszu polecenia, aby uruchomić oba aplikacje jednocześnie.  
  
 Ewentualnie przejdź do katalogi, które zawierają nowe PLiki wykonywalne i uruchom je sekwencyjnie.  
  
> [!NOTE]
> Przykład tworzy aplikacje konsolowe. Należy uruchomić i uruchom je w oknie wiersza polecenia, aby wyświetlić ich danych wyjściowych.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>
- <xref:System.IO.FileStream>
