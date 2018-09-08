---
title: Przykład technologii serializacji z tolerancją wersji
ms.date: 03/30/2017
ms.assetid: 2a183664-bfbf-4ff0-96f6-c836284ea916
ms.openlocfilehash: 34dccc9065c0100a01a7969a1fe762001e2999a9
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44210857"
---
# <a name="version-tolerant-serialization-technology-sample"></a>Przykład technologii serializacji z tolerancją wersji
[Pobierz przykładowe](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/VTS.zip.exe)  
  
 W przykładzie pokazano funkcje tolerancja wersji programu .NET serializacji. Próbka tworzy aplikacje, które używają różnych wersji <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> do serializacji i deserializacji danych. Niezależnie od obecności wersje różnych typów aplikacji bezproblemowo łączy. Aby uzyskać więcej informacji, zobacz [serializacja z tolerancją wersji](../../../docs/standard/serialization/version-tolerant-serialization.md).  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a>Aby skompilować przykład za pomocą wiersza polecenia  
  
1.  Otwórz okno wiersza polecenia i przejdź do jednej z podkatalogi specyficzny dla języka (w obszarze aplikację V1 lub V2) dla próbki.  
  
2.  Typ **msbuild.exe \<ver > application.sln** w wierszu polecenia (gdzie \<serwerów > jest v1 lub v2).  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Aby skompilować przykład za pomocą programu Visual Studio  
  
1.  Otwórz [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] i przejdź do jednej z podkatalogi specyficzny dla języka dla próbki.  
  
2.  Przejdź do podkatalogu V1 aplikacji w katalogu, który został wybrany w poprzednim kroku.  
  
3.  Kliknij dwukrotnie ikonę Application.sln V1 do otwierania tego pliku w programie Visual Studio.  
  
4.  Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
5.  Przejdź do podkatalogu aplikacji w wersji 2 i Powtórz dwa poprzednie kroki do tworzenia aplikacji w wersji 2.  
  
 Aplikacje zostanie utworzona w domyślnych podkatalogów \bin lub \bin\Debug ich katalogów odpowiednich projektu.  
  
### <a name="to-run-the-sample"></a>Aby uruchomić przykład  
  
1.  W oknie wiersza polecenia przejdź do wybranego podczas tworzenia aplikacji przykładowych podkatalogu specyficzny dla języka.  
  
2.  Typ **runme.cmd** w wierszu polecenia do uruchamiania obu aplikacji jednocześnie.  
  
 Ewentualnie przejdź do katalogi, które zawierają nowe PLiki wykonywalne i uruchom je sekwencyjnie.  
  
> [!NOTE]
>  Próbka tworzy aplikacji konsoli. Należy uruchomić i uruchom je w oknie wiersza polecenia, aby wyświetlić ich danych wyjściowych.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
- <xref:System.IO.FileStream>
