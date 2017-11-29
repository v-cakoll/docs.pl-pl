---
title: "Przykładowe technologii serializacji z tolerancją dla wersji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2a183664-bfbf-4ff0-96f6-c836284ea916
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e518d9c4477377e6d0d7e569a29efcf4801101fc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="version-tolerant-serialization-technology-sample"></a>Przykładowe technologii serializacji z tolerancją dla wersji
[Pobieranie próbki](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/VTS.zip.exe)  
  
 W przykładzie pokazano funkcje tolerancji wersji serializacji .NET. Próbka tworzy aplikacje używające różnych wersji <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> do serializowania i deserializowania danych. Niezależnie od obecności innego typu wersji aplikacji komunikują się bezproblemowo. Aby uzyskać więcej informacji, zobacz [serializacji z tolerancją dla wersji](../../../docs/standard/serialization/version-tolerant-serialization.md).  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a>Aby samodzielnie tworzyć przykładowy przy użyciu wiersza polecenia  
  
1.  Otwórz okno wiersza polecenia i przejdź do jednej z podkatalogi specyficzne dla języka (w obszarze aplikację V1 lub V2) przykładowej.  
  
2.  Typ **msbuild.exe \<ver > application.sln** w wierszu polecenia (gdzie \<ver > jest v1 lub v2).  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Aby samodzielnie tworzyć przykładowy przy użyciu programu Visual Studio  
  
1.  Otwórz [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] i przejdź do jednej z przykładowej podkatalogi specyficzny dla języka.  
  
2.  Przejdź do podkatalogu V1 aplikacji katalogu, który wybrano w poprzednim kroku.  
  
3.  Kliknij dwukrotnie ikonę Application.sln V1 otworzyć plik w programie Visual Studio.  
  
4.  Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
5.  Przejdź do podkatalogu aplikacji V2 i Powtórz dwa poprzednie kroki, aby skompilować aplikację V2.  
  
 Aplikacje zostaną skompilowane w podkatalogach \bin lub \bin\Debug domyślne katalogi ich odpowiednich projektu.  
  
### <a name="to-run-the-sample"></a>Aby uruchomić przykładowy  
  
1.  W oknie wiersza polecenia przejdź do podkatalogu specyficzny dla języka wybranego podczas tworzenia aplikacji przykładowej.  
  
2.  Typ **runme.cmd** w wierszu polecenia, aby uruchomić jednocześnie obydwu aplikacji.  
  
 Ewentualnie przejdź do katalogi, które zawierają nowe PLiki wykonywalne i uruchom je sekwencyjnie.  
  
> [!NOTE]
>  Przykład tworzy aplikacji konsoli. Należy uruchomić i uruchom je w oknie wiersza polecenia, aby wyświetlić ich danych wyjściowych.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
 <xref:System.IO.FileStream>
