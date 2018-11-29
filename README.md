Quiz 04
=

모든 퀴즈는 해당 강의중에 언급된 내용에서만 국한된다.  
퀴즈 답변이 모호하다고 생각한다면 해당 이유를 적고 본인이 생각하는 답을 작성하여 제출한다.  

0_1. 해당 퀴즈 git을 fork하여 답안을 작성하시오.  
0_2. 운영진의 공지를 확인하고 알맞은 branch로 답지를 pull request를 보내시오.  
1. follow 기능을 어떤 gem으로 구현하였는가?  
    답 :   gem 'acts_as_follower', github: 'tcocca/acts_as_follower', branch: 'master'
2. Comment 모델과 N:M 관계를 가지는 모델을 전부 쓰시오  
    답 :   user, article, artist, song
3. profile 유효성검사는 어떻게 하였는지 적으시오  
    답 :   validates :name, presence: true, length: { minimum:2, maximum: 30}#길이 최소한글자, 최대 30글자
           VALID_PHONE_NUMBER = /\A010([1-9]{1}[0-9]{3})([0-9]{4})\z/
            validates :mobile, presence: true, format: {with: VALID_PHONE_NUMBER}, uniqueness: true
4. 커스텀 helper를 사용한 기능은 무엇인지 모두 쓰시오  
    답 :   
profile.helper의
  def gravatar_url(email, size)
    gravatar = Digest::MD5::hexdigest(email).downcase
    url = "http://gravatar.com/avatar/#{gravatar}.png?s=#{size}"
  end

jukebox.helper의 
    def user_editable?
        if current_user.profile.role == 'admin'
            true
        elsif current_user.profile.role == 'editor'
            true
        else
            false
        end
    end
    
    
5. 파일 업로더는 어떤 방식으로 구현하였는가  
    답 :   gem 'carrierwave' 를 이용해서 cover_uploader.rb파일과 profile_img_uplader.rb파일을 만들어서 구현하였따.

6. controller 중 rendering view 로만 이루어진것은 무엇인지 모두 쓰시오   
    답 :   comments, participates

7. 강의중 게시글 본문의 에디터는 어떻게 구현하였는지 쓰시오  
    답 :   <%= render 'form', article: @article %> 
            render를 이용해서 구현하였다.(_form.html.erb파일을 따로 만들고 그것을 렌더해서)

8. 댓글은 어떻게 구현하였는지 쓰시오   
    답 :  gem 'acts_as_commentable' 젬을 이용해서 구현하였다.


9. 컨트롤러로 넘어오는 입력값을 어떻게 가공하여 모델로 넘겨주는지 쓰시오  
    답 :  private에 공통된(자주쓰는)코드를 쓰고, before_action으로 검사하여서.


10. 프로젝트의 root_url은 어디로 연결되어있는지 쓰시오
    답 : articles#index

11. article_url 의 method : get 요청에는 몇개의 html 페이지가 렌더링되있는지 적고 각각이 어떤 redering page 인지 적으시오  
    답 : 4개 
<%= render 'userUI' %>      #articles폴더 안의 _userUI.html.erb파일
<%= render 'like' %>        #articles폴더 안의 _like.html.erb파일
<%= render 'comments/form', commentable: @article %> #comments폴더 안의 _form.html.erb파일
<%= render 'comments/index', commentable: @article %> #comments폴더 안의 _index.html.erb파링

12. 본인의 보조강의 워크스페이스 github repo 주소를 적으시오  
깃헙에 없다면 새로 만들어서 링크를 제출하시오   
    답 : https://github.com/hyojin17/last_quiz.git