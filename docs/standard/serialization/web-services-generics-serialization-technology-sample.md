---
title: Przykład technologii serializacji danych ogólnych dla usług internetowych
ms.date: 03/30/2017
ms.assetid: cdc15ea4-f678-4729-8ebe-188ae720bef7
ms.openlocfilehash: 467bfe1fd9eb8a0222385c34cb29a90df00dc937
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960749"
---
# <a name="web-services-generics-serialization-technology-sample"></a>Przykład technologii serializacji danych ogólnych dla usług internetowych
[Pobierz przykład](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/GenericsSerialization.zip.exe)  
  
 Ten przykład pokazuje, jak używać i kontrolować serializację typów ogólnych w usługach ASP.NET Web Services.  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Aby skompilować przykład za pomocą programu Visual Studio  
  
1. Otwórz program Visual Studio i wybierz pozycję **Nowa witryna sieci Web** w menu **plik** .  
  
2. W oknie dialogowym **Nowa witryna sieci Web** wybierz w lewym okienku odpowiedni język programowania, a następnie w okienku po prawej stronie wybierz pozycję **usługa sieci Web ASP.NET**.  
  
3. Kliknij przycisk **Przeglądaj** i przejdź do podkatalogu \CS\GenericsService.  
  
4. Wybierz Service.asmx do otwierania tego PLiku w programie Visual Studio.  
  
5. W menu **Kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.  
  
> [!NOTE]
> Pierwszych pięć kroków na tej liście są opcjonalne. Środowisko uruchomieniowe programu .NET Framework automatycznie generuje razem usługi pierwszy sieci Web, gdy wymagane są usługi.  
  
> [!NOTE]
> Poniższe kroki są wymagane do utworzenia przykładu.  
  
1. Otwórz Eksploratora plików i przejdź do podkatalogu \CS  
  
2. Kliknij prawym przyciskiem myszy ikonę podkatalogu GenericsService, a następnie wybierz pozycję **udostępnianie i zabezpieczenia**.  
  
3. Na karcie **udostępnianie w sieci Web** wybierz pozycję **Udostępnij ten folder**.  
  
> [!IMPORTANT]
> Zwróć uwagę na nazwę katalogu wirtualnego, która jest wymieniona w okienku **aliasy** , ponieważ będzie potrzebna do uruchomienia przykładu.  
  
### <a name="to-build-the-sample-using-internet-information-services"></a>Aby skompilować przykład za pomocą Internet Information Services  
  
1. Otwórz przystawkę Zarządzanie **Internet Information Services** i rozwiń węzeł **witryny sieci Web**.  
  
2. Kliknij lewym przyciskiem myszy pozycję **Domyślna witryna sieci Web**, wybierz pozycję **Nowy**, a następnie wybierz pozycję **katalog wirtualny?** aby utworzyć **Kreatora tworzenia katalogów wirtualnych**.  
  
3. Kliknij przycisk **dalej**, wprowadź publiczny alias katalogu wirtualnego, a następnie kliknij przycisk **dalej**.  
  
4. Wprowadź ścieżkę do katalogu, w którym zapisano przykład (zwykle podkatalog \CS\GenericsService), a następnie kliknij przycisk **dalej**. Kliknij przycisk **dalej** , aby zakończyć pracę kreatora.  
  
> [!IMPORTANT]
> Zwróć uwagę na nazwę katalogu wirtualnego, która jest wymieniona w okienku **alias** , ponieważ będzie potrzebna do uruchomienia przykładu.  
  
### <a name="to-run-the-sample"></a>Aby uruchomić przykład  
  
1. Otwórz okno przeglądarki, a następnie wybierz jego paskiem adresu.  
  
2. Typ `http://localhost/[virtual directory]/Service.asmx`, gdzie `[virtual directory]` reprezentuje katalog wirtualny, który został utworzony podczas tworzenia przykładu.  
  
## <a name="remarks"></a>Uwagi  
 Przykład wyświetla domyślną stronę ASP.NET zawierającą linki do definicji usługi sieci Web. Można dostosować wyświetlanie oprócz modyfikacji kodu źródłowego usługi sieci Web. Aby uzyskać więcej informacji, zobacz [Tworzenie klientów usług sieci Web XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w3h45ebk(v=vs.100)).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Generic>
- <xref:System.Web.Services>
- <xref:System.Xml.Serialization>
- [Serializacja](../../../docs/standard/serialization/index.md)
- [Usługi sieci Web XML utworzone za pomocą ASP.NET i klientów usług sieci Web XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))
