---
title: My.Resources — Obiekt
ms.date: 07/20/2015
f1_keywords:
- My.Resources
- My.Resources.MyResources.ResourceManager
- My.Resources.MyResources.Culture
helpviewer_keywords:
- My.Resources object
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
ms.openlocfilehash: 2b7c82c31d2e31ccbf573cf1dfa138af2d99ce29
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372465"
---
# <a name="myresources-object"></a>My.Resources — Obiekt
Udostępnia właściwości i klasy do uzyskiwania dostępu do zasobów aplikacji.  
  
## <a name="remarks"></a>Uwagi  
 `My.Resources`Obiekt zapewnia dostęp do zasobów aplikacji i umożliwia dynamiczne pobieranie zasobów dla aplikacji. Aby uzyskać więcej informacji, zobacz [Zarządzanie zasobami aplikacji (.NET)](/visualstudio/ide/managing-application-resources-dotnet).  
  
 `My.Resources`Obiekt uwidacznia tylko zasoby globalne. Nie zapewnia dostępu do plików zasobów skojarzonych z formularzami. Musisz uzyskać dostęp do zasobów formularza z formularza.  
  
 Możesz uzyskać dostęp do plików zasobów specyficznych dla kultury aplikacji z `My.Resources` obiektu. Domyślnie `My.Resources` obiekt wyszukuje zasoby z pliku zasobów, który jest zgodny z kulturą we <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> właściwości. Można jednak zastąpić to zachowanie i określić określoną kulturę do użycia dla zasobów. Aby uzyskać więcej informacji, zobacz [zasoby w aplikacjach klasycznych](../../../framework/resources/index.md).  
  
## <a name="properties"></a>Właściwości  
 Właściwości `My.Resources` obiektu zapewniają dostęp tylko do odczytu do zasobów aplikacji. Aby dodać lub usunąć zasoby, użyj **projektanta projektu**. Dostęp do zasobów dodanych za pośrednictwem **projektanta projektu** można uzyskać za pomocą `My.Resources.` *resourceName*.  
  
 Możesz również dodać lub usunąć pliki zasobów, wybierając projekt w **Eksplorator rozwiązań** i klikając polecenie **Dodaj nowy element** lub **Dodaj istniejący element** z menu **projekt** . Dostęp do zasobów dodanych w ten sposób można uzyskać przy użyciu `My.Resources.` *resourceFileName* `.` *resourceName*nazwaplikuzasobów.  
  
 Każdy zasób ma nazwę, kategorię i wartość, a te ustawienia zasobów określają, w jaki sposób Właściwość uzyskiwania dostępu do zasobu jest wyświetlana w `My.Resources` obiekcie. Dla zasobów dodanych w **projektancie projektu**:  
  
- Nazwa Określa nazwę właściwości,  
  
- Dane zasobu to wartość właściwości,  
  
- Kategoria określa typ właściwości:  
  
|Kategoria|Typ danych właściwości|  
|---|---|  
|**Ciągi**|[Ciąg](../data-types/string-data-type.md)|  
|**Obrazy**|<xref:System.Drawing.Bitmap>|  
|**Ikony**|<xref:System.Drawing.Icon>|  
|**Audio**|<xref:System.IO.UnmanagedMemoryStream><br /><br /> <xref:System.IO.UnmanagedMemoryStream>Klasa pochodzi od <xref:System.IO.Stream> klasy, więc może być używana z metodami, które pobierają strumienie, takie jak <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> Metoda.|  
|**Files**|-   [Ciąg](../data-types/string-data-type.md) dla plików tekstowych.<br />-   <xref:System.Drawing.Bitmap>dla plików obrazów.<br />-   <xref:System.Drawing.Icon>dla plików ikon.<br />-   <xref:System.IO.UnmanagedMemoryStream>dla plików dźwiękowych.|  
|**Inne**|Określone przez informacje w kolumnie **Typ** projektanta.|  
  
## <a name="classes"></a>Klasy  
 `My.Resources`Obiekt uwidacznia każdy plik zasobów jako klasę z właściwościami udostępnionymi. Nazwa klasy jest taka sama jak nazwa pliku zasobu. Zgodnie z opisem w poprzedniej sekcji zasoby w pliku zasobów są ujawniane jako właściwości w klasie.  
  
## <a name="example"></a>Przykład  
 Ten przykład ustawia tytuł formularza na zasób ciągu o nazwie `Form1Title` w pliku zasobów aplikacji. Aby przykład działał, aplikacja musi mieć ciąg o nazwie `Form1Title` w pliku zasobów.  
  
 [!code-vb[VbVbalrMyResources#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#1)]  
  
## <a name="example"></a>Przykład  
 Ten przykład ustawia ikonę formularza na ikonę o nazwie `Form1Icon` , która jest przechowywana w pliku zasobów aplikacji. Aby przykład działał, aplikacja musi mieć ikonę o nazwie `Form1Icon` w pliku zasobów.  
  
 [!code-vb[VbVbalrMyResources#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#2)]  
  
## <a name="example"></a>Przykład  
 Ten przykład służy do ustawiania obrazu tła formularza do zasobu obrazu o nazwie `Form1Background` , który znajduje się w pliku zasobów aplikacji. Aby ten przykład działał, aplikacja musi mieć zasób obrazu o nazwie `Form1Background` w pliku zasobów.  
  
 [!code-vb[VbVbalrMyResources#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#3)]  
  
## <a name="example"></a>Przykład  
 Ten przykład odtwarza dźwięk zapisany jako zasób audio o nazwie `Form1Greeting` w pliku zasobów aplikacji. Aby przykład działał, aplikacja musi mieć zasób audio o nazwie `Form1Greeting` w pliku zasobów. Ta `My.Computer.Audio.Play` Metoda jest dostępna tylko dla aplikacji Windows Forms.  
  
 [!code-vb[VbVbalrMyResources#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#4)]  
  
## <a name="example"></a>Przykład  
 Ten przykład Pobiera wersję kultury języka francuskiego dla zasobu ciągu aplikacji. Zasób ma nazwę `Message` . Aby zmienić kulturę `My.Resources` używaną przez obiekt, użyjemy przykładu <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A> .  
  
 Aby ten przykład działał, aplikacja musi mieć ciąg o nazwie `Message` w pliku zasobów, a aplikacja powinna mieć wersję kultury języka francuskiego tego pliku zasobów Resources.fr-fr. resx. Jeśli aplikacja nie ma wersji pliku zasobów w języku francuskim, `My.Resource` obiekt pobiera zasób z pliku zasobów kultury domyślnej.  
  
 [!code-vb[VbVbalrMyResources#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#10)]  
  
## <a name="see-also"></a>Zobacz też

- [Zarządzanie zasobami aplikacji (.NET)](/visualstudio/ide/managing-application-resources-dotnet)
- [Zasoby w aplikacjach klasycznych](../../../framework/resources/index.md)
