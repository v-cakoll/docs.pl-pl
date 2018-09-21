---
title: Przykład technologii serializacji typów ogólnych usług sieci Web
ms.date: 03/30/2017
ms.assetid: cdc15ea4-f678-4729-8ebe-188ae720bef7
ms.openlocfilehash: b233ed4374231c7e7ff2b6617a63c4e4c94612c2
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46479549"
---
# <a name="web-services-generics-serialization-technology-sample"></a>Przykład technologii serializacji typów ogólnych usług sieci Web
[Pobierz przykładowe](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/GenericsSerialization.zip.exe)  
  
 W tym przykładzie przedstawiono sposób użycia i sterować serializacji rodzajowych w usługach sieci Web programu ASP.NET.  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Aby skompilować przykład za pomocą programu Visual Studio  
  
1.  Otwórz program Visual Studio i wybierz **nową witrynę sieci Web** z **pliku** menu.  
  
2.  W **nową witrynę sieci Web** okno dialogowe, wybierz w okienku po lewej stronie język programowania, a następnie w okienku po prawej stronie wybierz **usługi sieci Web ASP.NET**.  
  
3.  Kliknij przycisk **Przeglądaj** i przejdź do podkatalogu \CS\GenericsService.  
  
4.  Wybierz Service.asmx do otwierania tego PLiku w programie Visual Studio.  
  
5.  Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
> [!NOTE]
>  Pierwszych pięć kroków na tej liście są opcjonalne. Środowisko uruchomieniowe programu .NET Framework automatycznie generuje razem usługi pierwszy sieci Web, gdy wymagane są usługi.  
  
> [!NOTE]
>  Poniższe kroki są wymagane do utworzenia przykładu.  
  
1.  Otwórz [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] i przejdź do podkatalogu \CS.  
  
2.  Kliknij prawym przyciskiem myszy ikonę podkatalogu GenericsService, a następnie wybierz pozycję **udostępnianie i zabezpieczenia**.  
  
3.  W **udostępnianie w sieci Web** zaznacz **Udostępnij ten Folder**.  
  
> [!IMPORTANT]
>  Zwróć uwagę na nazwy katalogu wirtualnego, który znajduje się w **aliasy** okienka, ponieważ będzie potrzebny do uruchomienia przykładu.  
  
### <a name="to-build-the-sample-using-internet-information-services"></a>Aby skompilować przykład za pomocą Internetowych usług informacyjnych  
  
1.  Otwórz **Internetowe usługi informacyjne** zarządzania przystawki i rozwiń **witryn sieci Web**.  
  
2.  Kliknięcie lewym przyciskiem myszy **domyślna witryna sieci Web**, wybierz opcję **nowy**, a następnie wybierz pozycję **katalog wirtualny?** utworzyć **Kreatora tworzenia katalogów wirtualnych**.  
  
3.  Kliknij przycisk **dalej**, wprowadź alias publicznego dla katalogu wirtualnego, a kliknij **dalej**.  
  
4.  Wprowadź ścieżkę do katalogu, w którym zapisywane próbce (zwykle podkatalogu \CS\GenericsService), a następnie kliknij przycisk **dalej**. Kliknij przycisk **dalej** aby zakończyć działanie kreatora.  
  
> [!IMPORTANT]
>  Zwróć uwagę na nazwy katalogu wirtualnego, który znajduje się w **Alias** okienka, ponieważ będzie potrzebny do uruchomienia przykładu.  
  
### <a name="to-run-the-sample"></a>Aby uruchomić przykład  
  
1.  Otwórz okno przeglądarki, a następnie wybierz jego paskiem adresu.  
  
2.  Typ `http://localhost/[virtual directory]/Service.asmx`, gdzie `[virtual directory]` reprezentuje katalog wirtualny utworzony podczas tworzenia przykładu.  
  
## <a name="remarks"></a>Uwagi  
 Przykład przedstawia domyślna strona programu ASP.NET, który zawiera łącza do definicji usługi sieci Web. Można dostosować wyświetlanie Oprócz modyfikowania kodu źródłowego dla usługi sieci Web. Aby uzyskać więcej informacji, zobacz [klientów usługi sieci Web XML budynku](https://msdn.microsoft.com/library/c606f3cb-4111-45b4-ae42-9300420fa16c).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic>  
- <xref:System.Web.Services>  
- <xref:System.Xml.Serialization>  
- [Serializacja](../../../docs/standard/serialization/index.md)  
- [Usługi sieci Web XML utworzone za pomocą platformy ASP.NET i klientów usługi sieci Web XML](https://msdn.microsoft.com/library/1e64af78-d705-4384-b08d-591a45f4379c)
