# urdu-ocr-codesaviours-si26-Hania-
**Urdu OCR Project | Code Saviours SI-26 | Hania Emaan**
#Week 1

**Question/Answers**

**1.What is OCR (Optical Character Recognition)?**

OCR is a technology that allows computers to read text from images, scanned documents, or photographs and convert it into digital, editable text. It works by analyzing the shapes and patterns of characters in an image and matching them to known letters or symbols. This is what allows you to scan a printed page and turn it into a Word document, or search for text within a scanned PDF.

**2.Why is Urdu OCR harder than English OCR?**

Urdu is written in a cursive script where letters change shape depending on their position in a word (beginning, middle, or end), unlike English letters which stay mostly the same. Urdu also has no fixed baseline, meaning letters can appear above, below, or connected to each other in flowing, non-linear ways, making segmentation very difficult. Additionally, there is much less labeled Urdu text data available for training OCR models compared to the huge amount of English text data, so models often perform worse due to limited resources.

**3.What are 2 real-world situations where Urdu OCR would be useful?**

One situation is digitizing old Urdu newspapers, books, and historical government records so they can be searched, stored, and preserved digitally instead of deteriorating physically. Another situation is helping visually impaired Urdu readers by converting printed Urdu text into speech using text-to-speech systems, giving them access to information they otherwise couldn't read. Urdu OCR could also help automate data entry for Urdu-language forms, such as ID cards or handwritten applications, in government and banking systems across Pakistan.

#Week 2
## Why We Need a Better Model

**Test 1**
- Actual: فرشتے کا کردار اس کہانی کا کبھی بھی حصہ نہیں تھا
- Tesseract: ڈرخنے کاکردارا کہانی کان بھی جع نی تھا
- Issue: Wrong first word entirely, missing spaces between several words, "نہیں" dropped to "نی"

**Test 2**
- Actual: یہ آغا ابراہیم کا گھر "آغا ہاؤس" تین منزلہ عالیشان محل نما کوٹھی تھی۔
- Tesseract: یآنااھاتکا اگھر' آھا ڈی شس منزلہ خالیشان بل ماک یی
- Issue: Heavy word-merging, "عالیشان" misread as "خالیشان", large chunks dropped or replaced with gibberish

**Test 3**
- Actual: دل میں ایک کانٹا سا چبھا۔
- Tesseract: ول یس ای کفکا نا سا چھا۔
- Issue: "دل" misread as "ول", "میں" garbled to "یس ای", "کانٹا" corrupted to "کفکا"

**Test 4**
- Actual: "یہ کتاب کس کی ہے؟"
- Tesseract: من یقاب سس گی ے؟"
- Issue: Almost entirely different characters, barely resembles original

**Test 5**
- Actual: وہ چائے کے سپ لیتا خاموشی سے اسے دیکھتا رہا۔
- Tesseract: دہ جیائے ہ- لت خاموق سے!سے تا ۸
- Issue: "وہ" misread as "دہ", "خاموشی" corrupted to "خاموق", ending garbled into stray symbols and a number

  **Summary**

**Tesseract fails on Urdu because** it struggles to correctly segment and recognize Urdu's cursive, context-dependent letterforms, where each letter changes shape depending on its position within a word. Across all 5 test images, Tesseract consistently merged separate words together, substituted visually similar but incorrect characters, and in several cases produced text that barely resembled the original sentence at all. Even after preprocessing (grayscale, resizing, denoising, and adaptive binarization), Tesseract's accuracy remained poor, showing that the core issue lies in its underlying Urdu language model rather than image quality. This confirms that general-purpose OCR engines like Tesseract — built primarily for Latin scripts — are not reliable for Urdu without a dedicated, custom-trained model, which is exactly the problem this project sets out to solve.
