---
title: 'Porady: ustawianie poziomu dekompresji JPEG'
description: Dowiedz się, jak dostosować jakość obrazu JPEG, modyfikując jego poziom kompresji na Windows Forms.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], changing encoder parameters
- JPEG images [Windows Forms], setting quality level
ms.assetid: 4b9a74e3-9504-43c1-9f28-ace651d0772e
ms.openlocfilehash: 1f6a96e8a05fff40eb08da0ce318faa86a06cc3a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618717"
---
# <a name="how-to-set-jpeg-compression-level"></a>Porady: ustawianie poziomu dekompresji JPEG
Możesz chcieć zmodyfikować parametry obrazu, gdy zapisujesz obraz na dysku w celu zminimalizowania rozmiaru pliku lub poprawy jego jakości. Jakość obrazu JPEG można dostosować, modyfikując jego poziom kompresji. Aby określić poziom kompresji podczas zapisywania obrazu JPEG, należy utworzyć <xref:System.Drawing.Imaging.EncoderParameters> obiekt i przekazać go do <xref:System.Drawing.Image.Save%2A> metody <xref:System.Drawing.Image> klasy. Zainicjuj <xref:System.Drawing.Imaging.EncoderParameters> obiekt, aby miał tablicę składającą się z jednego <xref:System.Drawing.Imaging.EncoderParameter> . Podczas tworzenia <xref:System.Drawing.Imaging.EncoderParameter> , określ <xref:System.Drawing.Imaging.Encoder.Quality> koder i żądany poziom kompresji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod tworzy <xref:System.Drawing.Imaging.EncoderParameter> obiekt i zapisuje trzy obrazy JPEG. Każdy obraz JPEG jest zapisywany z innym poziomem jakości przez zmodyfikowanie `long` wartości przesłanej do <xref:System.Drawing.Imaging.EncoderParameter> konstruktora. Poziom jakości równy 0 odpowiada najwyższej kompresji, a poziom jakości 100 odpowiada najmniej kompresji.  
  
```csharp  
private void VaryQualityLevel()  
    {  
        // Get a bitmap. The using statement ensures objects  
        // are automatically disposed from memory after use.  
        using (Bitmap bmp1 = new Bitmap(@"C:\TestPhoto.jpg"))  
        {  
            ImageCodecInfo jpgEncoder = GetEncoder(ImageFormat.Jpeg);  
  
            // Create an Encoder object based on the GUID  
            // for the Quality parameter category.  
            System.Drawing.Imaging.Encoder myEncoder =  
                System.Drawing.Imaging.Encoder.Quality;  
  
            // Create an EncoderParameters object.  
            // An EncoderParameters object has an array of EncoderParameter  
            // objects. In this case, there is only one  
            // EncoderParameter object in the array.  
            EncoderParameters myEncoderParameters = new EncoderParameters(1);  
  
            EncoderParameter myEncoderParameter = new EncoderParameter(myEncoder, 50L);  
            myEncoderParameters.Param[0] = myEncoderParameter;  
            bmp1.Save(@"c:\TestPhotoQualityFifty.jpg", jpgEncoder, myEncoderParameters);  
  
            myEncoderParameter = new EncoderParameter(myEncoder, 100L);  
            myEncoderParameters.Param[0] = myEncoderParameter;  
            bmp1.Save(@"C:\TestPhotoQualityHundred.jpg", jpgEncoder, myEncoderParameters);  
  
            // Save the bitmap as a JPG file with zero quality level compression.  
            myEncoderParameter = new EncoderParameter(myEncoder, 0L);  
            myEncoderParameters.Param[0] = myEncoderParameter;  
            bmp1.Save(@"C:\TestPhotoQualityZero.jpg", jpgEncoder, myEncoderParameters);  
        }  
    }  
```  
  
```vb  
Private Sub VaryQualityLevel()  
    ' Get a bitmap. The Using statement ensures objects  
    ' are automatically disposed from memory after use.  
    Using bmp1 As New Bitmap("C:\test\TestPhoto.jpg")  
        Dim jpgEncoder As ImageCodecInfo = GetEncoder(ImageFormat.Jpeg)  
  
        ' Create an Encoder object based on the GUID  
        ' for the Quality parameter category.  
        Dim myEncoder As System.Drawing.Imaging.Encoder = System.Drawing.Imaging.Encoder.Quality  
  
        ' Create an EncoderParameters object.  
        ' An EncoderParameters object has an array of EncoderParameter  
        ' objects. In this case, there is only one  
        ' EncoderParameter object in the array.  
        Dim myEncoderParameters As New EncoderParameters(1)  
  
        Dim myEncoderParameter As New EncoderParameter(myEncoder, 50L)  
        myEncoderParameters.Param(0) = myEncoderParameter  
        bmp1.Save("c:\test\TestPhotoQualityFifty.jpg", jpgEncoder, myEncoderParameters)  
  
        myEncoderParameter = New EncoderParameter(myEncoder, 100L)  
        myEncoderParameters.Param(0) = myEncoderParameter  
        bmp1.Save("C:\test\TestPhotoQualityHundred.jpg", jpgEncoder, myEncoderParameters)  
  
        ' Save the bitmap as a JPG file with zero quality level compression.  
        myEncoderParameter = New EncoderParameter(myEncoder, 0L)  
        myEncoderParameters.Param(0) = myEncoderParameter  
        bmp1.Save("C:\test\TestPhotoQualityZero.jpg", jpgEncoder, myEncoderParameters)  
    End Using  
End Sub  
```  
  
```csharp  
private ImageCodecInfo GetEncoder(ImageFormat format)  
{  
    ImageCodecInfo[] codecs = ImageCodecInfo.GetImageDecoders();  
    foreach (ImageCodecInfo codec in codecs)  
    {  
        if (codec.FormatID == format.Guid)  
        {  
            return codec;  
        }  
    }  
    return null;  
}  
```  
  
```vb  
Private Function GetEncoder(ByVal format As ImageFormat) As ImageCodecInfo  
  
    Dim codecs As ImageCodecInfo() = ImageCodecInfo.GetImageDecoders()  
    Dim codec As ImageCodecInfo  
    For Each codec In codecs  
        If codec.FormatID = format.Guid Then  
            Return codec  
        End If  
    Next codec  
    Return Nothing  
  
End Function  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Aplikacja Windows Forms.  
  
- A <xref:System.Windows.Forms.PaintEventArgs> , który jest parametrem <xref:System.Windows.Forms.PaintEventHandler> .  
  
- Plik obrazu o nazwie `TestPhoto.jpg` i zlokalizowany w **c \\ :**.  
  
## <a name="see-also"></a>Zobacz także

- [Porady: określanie parametrów obsługiwanych przez koder](how-to-determine-the-parameters-supported-by-an-encoder.md)
- [Typy map bitowych](types-of-bitmaps.md)
- [Używanie kodeków obrazu w zarządzanym GDI+](using-image-encoders-and-decoders-in-managed-gdi.md)
