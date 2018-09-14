---
title: Przykład technologii serializacji podstawowej
ms.date: 03/30/2017
ms.assetid: 9d824e16-08d1-4a36-bc7f-2388c1f75f34
ms.openlocfilehash: 474eb8ded01a72182533a6d49397d7567447d64e
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45619097"
---
# <a name="basic-serialization-technology-sample"></a>Przykład technologii serializacji podstawowej
[Pobierz przykładowe](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/Basic.zip.exe)  
  
 Niniejszy przykład pokazuje możliwość języka wspólnego serializacji grafu obiektów w pamięci w strumieniu. W tym przykładzie można użyć dowolnego <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> lub <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> do serializacji. Połączonej listy wypełniany danymi, jest serializacji lub deserializacji z strumienia PLiku lub. W obu przypadkach zostanie wyświetlona lista, tak, aby zobaczyć wyniki. Połączonej listy jest typu `LinkedList`, typ zdefiniowany przez ten przykład.  
  
 Komentarzy w PLikach źródłowych kodu i build.proj uzyskać więcej informacji o serializacji.  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a>Aby skompilować przykład za pomocą wiersza polecenia  
  
1.  Przejdź do jednego z podkatalogi specyficzne dla języka w katalogu Technologies\Serialization\Runtime Serialization\Basic, za pomocą wiersza polecenia.  
  
2.  Typ **msbuild SerializationCS.sln**, **msbuild SerializationJSL.sln** lub **msbuild SerializationVB.sln**, w zależności od wybranych przez siebie język programowania, w Wiersz polecenia.  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Aby skompilować przykład za pomocą programu Visual Studio  
  
1.  Otwórz [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] i przejdź do jednej z podkatalogi specyficzny dla języka dla próbki.  
  
2.  Kliknij dwukrotnie ikonę PLiku SerializationCS.sln, SerializationJSL.sln lub SerializationVB.sln, w zależności od wybranych przez siebie język programowania, aby otworzyć go w programie Visual Studio.  
  
3.  W **kompilacji** menu, wybierz opcję **Kompiluj rozwiązanie**.  
  
 Przykładowa aplikacja zostanie utworzona w podkatalogu \bin lub \bin\Debug domyślny.  
  
### <a name="to-run-the-sample"></a>Aby uruchomić przykład  
  
1.  Przejdź do katalogu zawierającego wbudowanych PLiku wykonywalnego.  
  
2.  Typ **Serialization.exe**, wraz z wartościami parametru wymagasz, w wierszu polecenia.  
  
    > [!NOTE]
    >  W tym przykładzie tworzy aplikację konsoli. Należy uruchomić go za pomocą wiersza polecenia, aby można było wyświetlić dane wyjściowe.  
  
## <a name="remarks"></a>Uwagi  
 Przykładowa aplikacja akceptuje parametry wiersza polecenia wskazujące, której można przetestować chce wykonać. Do serializacji lista 10-węzłów, w pliku o nazwie **Test.xml** przy użyciu protokołu SOAP program formatujący, użyj parametrów **sx Test.xml 10**.  
  
 Na przykład:  
  
 **Serialize.exe - sx Test.xml 10**  
  
 Do deserializacji **Test.xml** plików z poprzedniego przykładu, użyj parametrów **dx Test.xml**.  
  
 Na przykład:  
  
 **Test.xml - dx Serialize.exe**  
  
 W dwóch przykładach w przełączniku wiersza polecenia "x" oznacza, że serializacji XML protokołu SOAP. "B" w tym miejscu służy do użycia serializacji binarnej. Jeśli chcesz spróbować serializacji z bardzo dużej liczby węzłów, można przekierować dane wyjściowe z konsoli do PLiku.  
  
 Na przykład:  
  
 **Serialize.exe - sb Test.bin 10000 > somefile.txt**  
  
 Następujące punktory Zwięźle opisz klas i technologie używane w tym przykładzie.  
  
-   Środowisko wykonawcze serializacji  
  
    -   <xref:System.Runtime.Serialization.IFormatter>Odnosi się do albo <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> lub <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> obiektu.  
  
    -   <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>Służy do serializacji połączonej listy w strumieniu w formacie binarnym. Binarny program formatujący używa formatu tylko <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> rozumie typu. Jednak dane są zwięzły.  
  
    -   <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>Służy do serializacji połączonej listy w strumieniu w formacie protokołu SOAP. Protokołu SOAP jest to standardowy format.  
  
-   We/Wy strumienia  
  
    -   <xref:System.IO.Stream>Służy do serializacji i deserializacji. Typ określonego strumienia używane w tym przykładzie jest <xref:System.IO.FileStream> typu. Jednak można użyć serializacji z dowolnego typu opracowane na podstawie <xref:System.IO.Stream>.  
  
    -   <xref:System.IO.File>Służy do tworzenia <xref:System.IO.FileStream> obiektów do odczytywania i tworzenia PLików na dysku.  
  
    -   <xref:System.IO.FileStream>Służy do serializacji i deserializacji połączonej listy.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO>  
- <xref:System.IO.File>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.Stream>  
- <xref:System.Random>  
- <xref:System.Runtime.Serialization>  
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>  
- <xref:System.Runtime.Serialization.IFormatter>  
- <xref:System.SerializableAttribute>  
- <xref:System.Xml.Serialization>  
- [Serializacja podstawowa](../../../docs/standard/serialization/basic-serialization.md)  
- [Serializacja binarna](../../../docs/standard/serialization/binary-serialization.md)  
- [Kontrolowanie serializacji XML przy użyciu atrybutów](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
- [Wprowadzenie do serializacji XML](../../../docs/standard/serialization/introducing-xml-serialization.md)  
- [Serializacja](../../../docs/standard/serialization/index.md)  
- [Serializacja XML i SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)
