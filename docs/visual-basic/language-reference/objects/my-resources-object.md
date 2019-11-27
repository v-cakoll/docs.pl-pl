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
ms.openlocfilehash: 7f5d81194123ad2151a494a3cb79aa1955e0fdad
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350326"
---
# <a name="myresources-object"></a>My.Resources — Obiekt
Udostępnia właściwości i klasy do uzyskiwania dostępu do zasobów aplikacji.  
  
## <a name="remarks"></a>Uwagi  
 Obiekt `My.Resources` zapewnia dostęp do zasobów aplikacji i umożliwia dynamiczne pobieranie zasobów dla aplikacji. Aby uzyskać więcej informacji, zobacz [Zarządzanie zasobami aplikacji (.NET)](/visualstudio/ide/managing-application-resources-dotnet).  
  
 Obiekt `My.Resources` uwidacznia tylko zasoby globalne. Nie zapewnia dostępu do plików zasobów skojarzonych z formularzami. Musisz uzyskać dostęp do zasobów formularza z formularza.  
  
 Możesz uzyskać dostęp do plików zasobów specyficznych dla kultury aplikacji z obiektu `My.Resources`. Domyślnie obiekt `My.Resources` wyszukuje zasoby z pliku zasobów, który jest zgodny z kulturą we właściwości <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A>. Można jednak zastąpić to zachowanie i określić określoną kulturę do użycia dla zasobów. Aby uzyskać więcej informacji, zobacz [zasoby w aplikacjach klasycznych](../../../framework/resources/index.md).  
  
## <a name="properties"></a>Właściwości  
 Właściwości obiektu `My.Resources` zapewniają dostęp tylko do odczytu do zasobów aplikacji. Aby dodać lub usunąć zasoby, użyj **projektanta projektu**. Dostęp do zasobów dodanych za pośrednictwem **projektanta projektu** można uzyskać przy użyciu `My.Resources.`*resourceName*.  
  
 Możesz również dodać lub usunąć pliki zasobów, wybierając projekt w **Eksplorator rozwiązań** i klikając polecenie **Dodaj nowy element** lub **Dodaj istniejący element** z menu **projekt** . Aby uzyskać dostęp do zasobów dodanych w ten sposób, użyj `My.Resources.`*nazwaplikuzasobów*`.`*resourceName*.  
  
 Każdy zasób ma nazwę, kategorię i wartość, a te ustawienia zasobów określają, w jaki sposób Właściwość uzyskiwania dostępu do zasobu jest wyświetlana w obiekcie `My.Resources`. Dla zasobów dodanych w **projektancie projektu**:  
  
- Nazwa Określa nazwę właściwości,  
  
- Dane zasobu to wartość właściwości,  
  
- Kategoria określa typ właściwości:  
  
|Kategoria|Typ danych właściwości|  
|---|---|  
|**Ciągi**|[Ciąg](../../../visual-basic/language-reference/data-types/string-data-type.md)|  
|**Obrazy**|<xref:System.Drawing.Bitmap>|  
|**Ikony**|<xref:System.Drawing.Icon>|  
|**Audio**|<xref:System.IO.UnmanagedMemoryStream><br /><br /> Klasa <xref:System.IO.UnmanagedMemoryStream> dziedziczy z klasy <xref:System.IO.Stream>, dlatego może być używana z metodami, które pobierają strumienie, takie jak Metoda <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>.|  
|**Pliki**|-   [ciąg](../../../visual-basic/language-reference/data-types/string-data-type.md) dla plików tekstowych.<br />-   <xref:System.Drawing.Bitmap> dla plików obrazów.<br />-   <xref:System.Drawing.Icon> dla plików ikon.<br />-   <xref:System.IO.UnmanagedMemoryStream> plików dźwiękowych.|  
|**Inne**|Określone przez informacje w kolumnie **Typ** projektanta.|  
  
## <a name="classes"></a>Klasy  
 Obiekt `My.Resources` uwidacznia każdy plik zasobów jako klasę z właściwościami udostępnionymi. Nazwa klasy jest taka sama jak nazwa pliku zasobu. Zgodnie z opisem w poprzedniej sekcji zasoby w pliku zasobów są ujawniane jako właściwości w klasie.  
  
## <a name="example"></a>Przykład  
 Ten przykład ustawia tytuł formularza na zasób ciągu o nazwie `Form1Title` w pliku zasobów aplikacji. Aby przykład działał, aplikacja musi mieć ciąg o nazwie `Form1Title` w pliku zasobów.  
  
 [!code-vb[VbVbalrMyResources#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#1)]  
  
## <a name="example"></a>Przykład  
 Ten przykład ustawia ikonę formularza na ikonę o nazwie `Form1Icon`, która jest przechowywana w pliku zasobów aplikacji. Aby przykład działał, aplikacja musi mieć ikonę o nazwie `Form1Icon` w jej pliku zasobów.  
  
 [!code-vb[VbVbalrMyResources#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#2)]  
  
## <a name="example"></a>Przykład  
 Ten przykład służy do ustawiania obrazu tła formularza do zasobu obrazu o nazwie `Form1Background`, który znajduje się w pliku zasobów aplikacji. Aby ten przykład działał, aplikacja musi mieć zasób obrazu o nazwie `Form1Background` w pliku zasobów.  
  
 [!code-vb[VbVbalrMyResources#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#3)]  
  
## <a name="example"></a>Przykład  
 Ten przykład odtwarza dźwięk zapisany jako zasób audio o nazwie `Form1Greeting` w pliku zasobów aplikacji. Aby przykład działał, aplikacja musi mieć zasób audio o nazwie `Form1Greeting` w pliku zasobów. Metoda `My.Computer.Audio.Play` jest dostępna tylko dla aplikacji Windows Forms.  
  
 [!code-vb[VbVbalrMyResources#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#4)]  
  
## <a name="example"></a>Przykład  
 Ten przykład Pobiera wersję kultury języka francuskiego dla zasobu ciągu aplikacji. Zasób ma nazwę `Message`. Aby zmienić kulturę używaną przez obiekt `My.Resources`, w przykładzie używane jest <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>.  
  
 Aby ten przykład działał, aplikacja musi mieć ciąg o nazwie `Message` w pliku zasobów, a aplikacja powinna mieć wersję języka francuskiego tego pliku zasobu, Resources.fr-FR. resx. Jeśli aplikacja nie ma wersji pliku zasobów w języku francuskim, obiekt `My.Resource` pobiera zasób z pliku zasobów kultury domyślnej.  
  
 [!code-vb[VbVbalrMyResources#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#10)]  
  
## <a name="see-also"></a>Zobacz także

- [Zarządzanie zasobami aplikacji (.NET)](/visualstudio/ide/managing-application-resources-dotnet)
- [Zasoby w aplikacjach klasycznych](../../../framework/resources/index.md)
