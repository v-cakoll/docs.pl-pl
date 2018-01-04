---
title: "Przykład technologii podstawowe serializacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d824e16-08d1-4a36-bc7f-2388c1f75f34
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c3d269b7603c63db73fdcbab91b777e69b228cc9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="basic-serialization-technology-sample"></a>Przykład technologii podstawowe serializacji
[Pobieranie próbki](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/Basic.zip.exe)  
  
 W przykładzie pokazano możliwości środowisko uruchomieniowe języka wspólnego firmy do serializacji obiektu wykresu w pamięci w strumieniu. W tym przykładzie można użyć dowolnego <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> lub <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> do serializacji. Połączonej listy wypełniany danymi, jest serializacji lub deserializacji z strumienia PLiku lub. W obu przypadkach zostanie wyświetlona lista, dzięki czemu można wyświetlić wyniki. Jest typu listy połączonej `LinkedList`, typ zdefiniowany w tym przykładzie.  
  
 Komentarzy w PLikach źródłowych kodu i build.proj uzyskać więcej informacji o serializacji.  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a>Aby samodzielnie tworzyć przykładowy przy użyciu wiersza polecenia  
  
1.  Przejdź do jednego z podkatalogi specyficzne dla języka w katalogu Technologies\Serialization\Runtime Serialization\Basic, za pomocą wiersza polecenia.  
  
2.  Typ **msbuild SerializationCS.sln**, **msbuild SerializationJSL.sln** lub **msbuild SerializationVB.sln**w oparciu o wybór język programowania, w Wiersz polecenia.  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Aby samodzielnie tworzyć przykładowy przy użyciu programu Visual Studio  
  
1.  Otwórz [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] i przejdź do jednej z przykładowej podkatalogi specyficzny dla języka.  
  
2.  Kliknij dwukrotnie ikonę PLiku SerializationCS.sln, SerializationJSL.sln lub SerializationVB.sln, w zależności od wybranych przez siebie język programowania, aby otworzyć go w programie Visual Studio.  
  
3.  W **kompilacji** menu, wybierz opcję **Kompiluj rozwiązanie**.  
  
 Przykładowa aplikacja zostanie utworzona w podkatalogu \bin lub \bin\Debug domyślne.  
  
### <a name="to-run-the-sample"></a>Aby uruchomić przykładowy  
  
1.  Przejdź do katalogu zawierającego wbudowanych PLiku wykonywalnego.  
  
2.  Typ **Serialization.exe**, wraz z wartościami parametrów wymaganych, w wierszu polecenia.  
  
    > [!NOTE]
    >  Ten przykład tworzy aplikacji konsoli. Należy uruchomić go za pomocą wiersza polecenia, aby można było wyświetlić dane wyjściowe.  
  
## <a name="remarks"></a>Uwagi  
 Przykładowa aplikacja akceptuje wskazujący, który można przetestować parametry wiersza polecenia chcesz wykonać. Do serializacji listę 10 węzła w pliku o nazwie **Test.xml** przy użyciu elementu formatującego SOAP, użyj parametrów **sx Test.xml 10**.  
  
 Na przykład:  
  
 **Serialize.exe - sx Test.xml 10**  
  
 Do deserializacji **Test.xml** pliku z poprzedniego przykładu, użyj parametrów **dx Test.xml**.  
  
 Na przykład:  
  
 **Test.xml - dx Serialize.exe**  
  
 W dwóch przykładach "x" przełącznika wiersza polecenia oznacza, że chcesz serializacji XML protokołu SOAP. "B" można użyć w tym miejscu można użyć serializacji binarnej. Jeśli chcesz spróbować serializacji z bardzo dużej liczby węzłów, można przekierować dane wyjściowe z konsoli do PLiku.  
  
 Na przykład:  
  
 **Serialize.exe - sb Test.bin 10000 > somefile.txt**  
  
 Następujące punktory krótko opisano klasy i technologie używane w tym przykładzie.  
  
-   Środowisko wykonawcze serializacji  
  
    -   <xref:System.Runtime.Serialization.IFormatter>Odnosi się do albo <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> lub <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> obiektu.  
  
    -   <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>Służy do serializacji połączonej listy w strumieniu w formacie binarnym. Binarny program formatujący używa formatu tylko <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> rozumie typu. Jednak dane są zwięzły.  
  
    -   <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>Służy do serializacji połączonej listy w strumieniu w formacie protokołu SOAP. Protokołu SOAP jest to standardowy format.  
  
-   We/Wy strumienia  
  
    -   <xref:System.IO.Stream>Służy do serializacji i deserializacji. Typ określonego strumienia używane w tym przykładzie jest <xref:System.IO.FileStream> typu. Jednak można użyć serializacji z dowolnego typu opracowane na podstawie <xref:System.IO.Stream>.  
  
    -   <xref:System.IO.File>Służy do tworzenia <xref:System.IO.FileStream> obiektów do odczytywania i tworzenia PLików na dysku.  
  
    -   <xref:System.IO.FileStream>Służy do serializacji i deserializacji połączonej listy.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO>  
 <xref:System.IO.File>  
 <xref:System.IO.FileStream>  
 <xref:System.IO.Stream>  
 <xref:System.Random>  
 <xref:System.Runtime.Serialization>  
 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>  
 <xref:System.Runtime.Serialization.IFormatter>  
 <xref:System.SerializableAttribute>  
 <xref:System.Xml.Serialization>  
 [Serializacja podstawowa](../../../docs/standard/serialization/basic-serialization.md)  
 [Serializacja binarna](../../../docs/standard/serialization/binary-serialization.md)  
 [Kontrolowanie serializacji XML przy użyciu atrybutów](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
 [Wprowadzenie do serializacji XML](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [Serializacja](../../../docs/standard/serialization/index.md)  
 [Serializacja XML i SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)
