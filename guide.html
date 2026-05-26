/**
 * RGB三原色分解体験サイト - JavaScriptメイン機能
 * 高校生向け教育Webサイト
 */

class RGBSeparator {
    constructor() {
        this.fileInput = document.getElementById('fileInput');
        this.uploadBox = document.getElementById('uploadBox');
        this.resultsArea = document.getElementById('resultsArea');
        this.downloadBtn = document.getElementById('downloadBtn');
        this.resetBtn = document.getElementById('resetBtn');
        
        this.originalCanvas = document.getElementById('originalCanvas');
        this.redCanvas = document.getElementById('redCanvas');
        this.greenCanvas = document.getElementById('greenCanvas');
        this.blueCanvas = document.getElementById('blueCanvas');
        
        this.currentImageData = null;
        
        this.initEventListeners();
        this.addSmoothScrolling();
    }

    initEventListeners() {
        // ファイル選択イベント
        this.fileInput.addEventListener('change', (e) => this.handleFileSelect(e));
        
        // ドラッグ&ドロップイベント
        this.uploadBox.addEventListener('dragover', (e) => this.handleDragOver(e));
        this.uploadBox.addEventListener('dragleave', (e) => this.handleDragLeave(e));
        this.uploadBox.addEventListener('drop', (e) => this.handleDrop(e));
        this.uploadBox.addEventListener('click', () => this.fileInput.click());
        
        // ボタンイベント
        this.downloadBtn.addEventListener('click', () => this.downloadSeparatedImages());
        this.resetBtn.addEventListener('click', () => this.resetInterface());
    }

    addSmoothScrolling() {
        // ナビゲーションのスムーススクロール
        document.querySelectorAll('.nav a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', (e) => {
                e.preventDefault();
                const target = document.querySelector(anchor.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });
    }

    handleDragOver(e) {
        e.preventDefault();
        this.uploadBox.classList.add('dragover');
    }

    handleDragLeave(e) {
        e.preventDefault();
        this.uploadBox.classList.remove('dragover');
    }

    handleDrop(e) {
        e.preventDefault();
        this.uploadBox.classList.remove('dragover');
        
        const files = e.dataTransfer.files;
        if (files.length > 0) {
            this.processFile(files[0]);
        }
    }

    handleFileSelect(e) {
        const file = e.target.files[0];
        if (file) {
            this.processFile(file);
        }
    }

    processFile(file) {
        // ファイル検証
        if (!this.validateFile(file)) {
            return;
        }

        this.showMessage('画像を読み込み中...', 'info');
        
        const reader = new FileReader();
        reader.onload = (e) => {
            const img = new Image();
            img.onload = () => {
                this.processImage(img);
                this.hideMessage();
            };
            img.onerror = () => {
                this.showMessage('画像の読み込みに失敗しました。別の画像を試してください。', 'error');
            };
            img.src = e.target.result;
        };
        reader.onerror = () => {
            this.showMessage('ファイルの読み込みに失敗しました。', 'error');
        };
        reader.readAsDataURL(file);
    }

    validateFile(file) {
        // ファイルタイプチェック
        const allowedTypes = ['image/jpeg', 'image/jpg', 'image/png', 'image/gif'];
        if (!allowedTypes.includes(file.type)) {
            this.showMessage('対応していないファイル形式です。JPEG、PNG、GIFファイルを選択してください。', 'error');
            return false;
        }

        // ファイルサイズチェック（5MB制限）
        const maxSize = 5 * 1024 * 1024; // 5MB
        if (file.size > maxSize) {
            this.showMessage('ファイルサイズが大きすぎます。5MB以下の画像を選択してください。', 'error');
            return false;
        }

        return true;
    }

    processImage(img) {
        try {
            // 画像サイズを適切にリサイズ
            const maxSize = 600;
            const { width, height } = this.calculateDisplaySize(img.width, img.height, maxSize);
            
            // 元画像をキャンバスに描画
            this.drawImageToCanvas(this.originalCanvas, img, width, height);
            
            // RGB分解処理
            this.separateRGBChannels(img, width, height);
            
            // 結果エリアを表示
            this.resultsArea.style.display = 'block';
            
            // 結果エリアまでスクロール
            this.resultsArea.scrollIntoView({ behavior: 'smooth', block: 'start' });
            
            this.showMessage('RGB分解が完了しました！各チャンネルの違いを確認してみてください。', 'success');
            
            // 3秒後にメッセージを消す
            setTimeout(() => this.hideMessage(), 3000);
            
        } catch (error) {
            console.error('画像処理エラー:', error);
            this.showMessage('画像の処理中にエラーが発生しました。', 'error');
        }
    }

    calculateDisplaySize(originalWidth, originalHeight, maxSize) {
        let width = originalWidth;
        let height = originalHeight;
        
        // 最大サイズを超える場合はリサイズ
        if (width > maxSize || height > maxSize) {
            const ratio = Math.min(maxSize / width, maxSize / height);
            width = Math.floor(width * ratio);
            height = Math.floor(height * ratio);
        }
        
        return { width, height };
    }

    drawImageToCanvas(canvas, img, width, height) {
        canvas.width = width;
        canvas.height = height;
        const ctx = canvas.getContext('2d');
        ctx.drawImage(img, 0, 0, width, height);
        return ctx.getImageData(0, 0, width, height);
    }

    separateRGBChannels(img, width, height) {
        // 各チャンネル用のキャンバスを設定
        this.redCanvas.width = width;
        this.redCanvas.height = height;
        this.greenCanvas.width = width;
        this.greenCanvas.height = height;
        this.blueCanvas.width = width;
        this.blueCanvas.height = height;

        // コンテキストを取得
        const originalCtx = this.originalCanvas.getContext('2d');
        const redCtx = this.redCanvas.getContext('2d');
        const greenCtx = this.greenCanvas.getContext('2d');
        const blueCtx = this.blueCanvas.getContext('2d');

        // 画像データを取得
        originalCtx.drawImage(img, 0, 0, width, height);
        const imageData = originalCtx.getImageData(0, 0, width, height);
        const data = imageData.data;

        // RGB各チャンネル用の画像データを作成
        const redData = new ImageData(width, height);
        const greenData = new ImageData(width, height);
        const blueData = new ImageData(width, height);

        // ピクセルごとに処理
        for (let i = 0; i < data.length; i += 4) {
            const r = data[i];     // 赤
            const g = data[i + 1]; // 緑
            const b = data[i + 2]; // 青
            const a = data[i + 3]; // アルファ（透明度）

            // 赤チャンネル（赤色で表示）
            redData.data[i] = r;     // 赤チャンネルの値をそのまま赤に
            redData.data[i + 1] = 0; // 緑は0
            redData.data[i + 2] = 0; // 青は0
            redData.data[i + 3] = a; // アルファ

            // 緑チャンネル（緑色で表示）
            greenData.data[i] = 0;     // 赤は0
            greenData.data[i + 1] = g; // 緑チャンネルの値をそのまま緑に
            greenData.data[i + 2] = 0; // 青は0
            greenData.data[i + 3] = a; // アルファ

            // 青チャンネル（青色で表示）
            blueData.data[i] = 0;     // 赤は0
            blueData.data[i + 1] = 0; // 緑は0
            blueData.data[i + 2] = b; // 青チャンネルの値をそのまま青に
            blueData.data[i + 3] = a; // アルファ
        }

        // 各チャンネルの画像データをキャンバスに描画
        redCtx.putImageData(redData, 0, 0);
        greenCtx.putImageData(greenData, 0, 0);
        blueCtx.putImageData(blueData, 0, 0);

        // データを保存（ダウンロード用）
        this.currentImageData = {
            original: this.originalCanvas.toDataURL('image/png'),
            red: this.redCanvas.toDataURL('image/png'),
            green: this.greenCanvas.toDataURL('image/png'),
            blue: this.blueCanvas.toDataURL('image/png')
        };
    }

    downloadSeparatedImages() {
        if (!this.currentImageData) {
            this.showMessage('ダウンロードする画像がありません。', 'error');
            return;
        }

        try {
            // 各チャンネルの画像をダウンロード
            this.downloadImage(this.currentImageData.red, 'red-channel.png');
            this.downloadImage(this.currentImageData.green, 'green-channel.png');
            this.downloadImage(this.currentImageData.blue, 'blue-channel.png');
            
            this.showMessage('画像のダウンロードが開始されました！', 'success');
        } catch (error) {
            console.error('ダウンロードエラー:', error);
            this.showMessage('ダウンロード中にエラーが発生しました。', 'error');
        }
    }

    downloadImage(dataURL, filename) {
        const link = document.createElement('a');
        link.download = filename;
        link.href = dataURL;
        document.body.appendChild(link);
        link.click();
        document.body.removeChild(link);
    }

    resetInterface() {
        // インターフェースをリセット
        this.resultsArea.style.display = 'none';
        this.fileInput.value = '';
        this.currentImageData = null;
        this.hideMessage();
        
        // アップロードエリアまでスクロール
        document.getElementById('experience').scrollIntoView({ 
            behavior: 'smooth', 
            block: 'start' 
        });
    }

    showMessage(text, type = 'info') {
        // 既存のメッセージを削除
        this.hideMessage();
        
        const messageDiv = document.createElement('div');
        messageDiv.className = `message ${type}-message`;
        messageDiv.textContent = text;
        messageDiv.style.position = 'fixed';
        messageDiv.style.top = '20px';
        messageDiv.style.left = '50%';
        messageDiv.style.transform = 'translateX(-50%)';
        messageDiv.style.zIndex = '1000';
        messageDiv.style.padding = '1rem 2rem';
        messageDiv.style.borderRadius = '8px';
        messageDiv.style.fontWeight = '500';
        messageDiv.style.boxShadow = '0 4px 15px rgba(0, 0, 0, 0.2)';
        
        if (type === 'error') {
            messageDiv.style.background = '#ff6b6b';
            messageDiv.style.color = 'white';
        } else if (type === 'success') {
            messageDiv.style.background = '#4ecdc4';
            messageDiv.style.color = 'white';
        } else {
            messageDiv.style.background = '#667eea';
            messageDiv.style.color = 'white';
        }
        
        document.body.appendChild(messageDiv);
        
        // フェードイン効果
        messageDiv.style.opacity = '0';
        messageDiv.style.transition = 'opacity 0.3s ease';
        setTimeout(() => messageDiv.style.opacity = '1', 10);
    }

    hideMessage() {
        const existingMessage = document.querySelector('.message');
        if (existingMessage) {
            existingMessage.style.opacity = '0';
            setTimeout(() => {
                if (existingMessage.parentNode) {
                    existingMessage.parentNode.removeChild(existingMessage);
                }
            }, 300);
        }
    }
}

// 教育的なインタラクション機能
class EducationalFeatures {
    constructor() {
        this.initColorDemos();
        this.initImageExamples();
    }

    initColorDemos() {
        // RGB値のインタラクティブな説明
        const colorDemos = document.querySelectorAll('.color-demo');
        
        colorDemos.forEach(demo => {
            demo.addEventListener('mouseenter', () => {
                demo.style.transform = 'scale(1.1) rotate(5deg)';
                demo.style.transition = 'all 0.3s ease';
            });
            
            demo.addEventListener('mouseleave', () => {
                demo.style.transform = 'scale(1) rotate(0deg)';
            });
        });
    }

    initImageExamples() {
        // 実例カードのホバー効果で詳細説明を表示
        const exampleCards = document.querySelectorAll('.example-card');
        
        exampleCards.forEach(card => {
            card.addEventListener('mouseenter', () => {
                card.style.background = 'linear-gradient(135deg, #f8f9ff, #e8f4f8)';
            });
            
            card.addEventListener('mouseleave', () => {
                card.style.background = 'var(--bg-light)';
            });
        });
    }
}

// 進捗表示機能
class ProgressIndicator {
    constructor() {
        this.createProgressIndicator();
    }

    createProgressIndicator() {
        const sections = ['theory', 'experience', 'examples', 'learning'];
        let currentSection = 0;

        window.addEventListener('scroll', () => {
            sections.forEach((sectionId, index) => {
                const section = document.getElementById(sectionId);
                if (section) {
                    const rect = section.getBoundingClientRect();
                    if (rect.top <= window.innerHeight / 2 && rect.bottom >= window.innerHeight / 2) {
                        currentSection = index;
                        this.updateNavActiveState(sectionId);
                    }
                }
            });
        });
    }

    updateNavActiveState(activeSectionId) {
        // ナビゲーションの現在のセクションをハイライト
        const navLinks = document.querySelectorAll('.nav a');
        navLinks.forEach(link => {
            link.style.background = '';
            link.style.color = 'var(--text-dark)';
            
            if (link.getAttribute('href') === `#${activeSectionId}`) {
                link.style.background = 'var(--primary-color)';
                link.style.color = 'var(--white)';
            }
        });
    }
}

// アプリケーション初期化
document.addEventListener('DOMContentLoaded', () => {
    // メイン機能を初期化
    new RGBSeparator();
    new EducationalFeatures();
    new ProgressIndicator();
    
    // ページ読み込み完了時のウェルカムメッセージ
    setTimeout(() => {
        console.log('🎨 RGB三原色分解体験サイトへようこそ！');
        console.log('📸 画像をアップロードしてRGB分解を体験してください');
    }, 1000);
});

// エラーハンドリング
window.addEventListener('error', (e) => {
    console.error('アプリケーションエラー:', e.error);
});

// Canvas APIサポートチェック
if (!document.createElement('canvas').getContext) {
    document.addEventListener('DOMContentLoaded', () => {
        document.body.innerHTML = `
            <div style="text-align: center; padding: 2rem; font-family: Arial, sans-serif;">
                <h2>⚠️ ブラウザが対応していません</h2>
                <p>このサイトを利用するには、Canvas APIに対応したブラウザが必要です。</p>
                <p>Chrome、Firefox、Safari、Edgeなどの最新ブラウザをご利用ください。</p>
            </div>
        `;
    });
}